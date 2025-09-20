<script setup>
import { ref, computed, onMounted } from 'vue'

const hamleler = ['Taş', 'Kağıt', 'Makas']
const tursayisi = ref(1)
const oyuncuSkor = ref(0)
const bilgisayarSkor = ref(0)
const oyuncuHamle = ref('')
const bilgisayarHamle = ref('')
const oyunDurumu = ref('')
const oyunSonucu = ref('')
const oyunBasladi = ref(false)
const tur = ref(0)
const kurallarGoster = ref(true)

onMounted(() => {
    kurallarGoster.value = true
})

function kurallarKapat() {
    kurallarGoster.value = false
}

const oyunBitti = computed(() => {
    return tur.value >= tursayisi.value || oyuncuSkor.value > tursayisi.value / 2 || bilgisayarSkor.value > tursayisi.value / 2
})

function bilgisayarHamlesiSec() {
    const index = Math.floor(Math.random() * hamleler.length)
    return hamleler[index]
}

function turOyna(oyuncuSecimi) {
    if (oyunBitti.value) return
    
    if (navigator.vibrate) {
        navigator.vibrate(50)
    }
    
    oyuncuHamle.value = oyuncuSecimi
    bilgisayarHamle.value = bilgisayarHamlesiSec()
    
    let sonuc = ''
    if (oyuncuSecimi === bilgisayarHamle.value) {
        sonuc = 'Berabere!'
        oyunDurumu.value = `${oyuncuSecimi} vs ${bilgisayarHamle.value} - Berabere!`
    } else if (
        (oyuncuSecimi === 'Taş' && bilgisayarHamle.value === 'Makas') ||
        (oyuncuSecimi === 'Kağıt' && bilgisayarHamle.value === 'Taş') ||
        (oyuncuSecimi === 'Makas' && bilgisayarHamle.value === 'Kağıt')
    ) {
        oyuncuSkor.value++
        sonuc = 'Kazandınız!'
        oyunDurumu.value = `${oyuncuSecimi} vs ${bilgisayarHamle.value} - ${sonuc}`
    } else {
        bilgisayarSkor.value++
        sonuc = 'Kaybettiniz!'
        oyunDurumu.value = `${oyuncuSecimi} vs ${bilgisayarHamle.value} - ${sonuc}`
    }
    
    tur.value++

    if (oyunBitti.value) {
        if (oyuncuSkor.value > bilgisayarSkor.value) {
            oyunSonucu.value = 'Tebrikler! Oyunu kazandınız!'
        } else if (bilgisayarSkor.value > oyuncuSkor.value) {
            oyunSonucu.value = 'Bilgisayar kazandı!  :('
        } else {
            oyunSonucu.value = 'Oyun berabere bitti!'
        }
    }
}

function oyunuBaslat() {
    oyunBasladi.value = true
}

function oyunuYenidenBaslat() {
    oyuncuSkor.value = 0
    bilgisayarSkor.value = 0
    tur.value = 0
    oyuncuHamle.value = ''
    bilgisayarHamle.value = ''
    oyunDurumu.value = ''
    oyunSonucu.value = ''
    oyunBasladi.value = false
}

function handleTouchStart(event) {
    event.target.style.transform = 'scale(0.95)'
    event.target.style.opacity = '0.8'
}

function handleTouchEnd(event) {
    setTimeout(() => {
        event.target.style.transform = ''
        event.target.style.opacity = ''
    }, 150)
}
</script>


<template>
    <div v-if="kurallarGoster" class="modal-overlay">
        <div class="modal-dialog">
            <div class="modal-header">
                <h2>TAŞ KAĞIT MAKAS OYUNU</h2>
            </div>
            <div class="modal-body">
                <div class="kurallar-bolumu">
                    <h3>OYUN KURALLARI:</h3>
                    <ul>
                        <li>Taş, Makas'ı yener</li>
                        <li>Makas, Kağıt'ı yener</li>
                        <li>Kağıt, Taş'ı yener</li>
                    </ul>
                </div>
                
                <div class="nasil-oynanir-bolumu">
                    <h3>NASIL OYNANIR:</h3>
                    <ol>
                        <li>Tur sayısını seçin (1-10)</li>
                        <li>Oyunu başlatın</li>
                        <li>TAŞ, KAĞIT veya MAKAS butonuna tıklayın</li>
                        <li>Bilgisayar da rastgele hamle yapar</li>
                        <li>En çok kazanan oyunu alır</li>
                    </ol>
                </div>
                
                <div class="iyi-oyunlar">
                    <p>İyi oyunlar!</p>
                </div>
            </div>
            <div class="modal-footer">
                <button @click="kurallarKapat" class="modal-btn" @touchstart="handleTouchStart" @touchend="handleTouchEnd">Tamamdır, Başlayalım!</button>
            </div>
        </div>
    </div>

    <div id="app">
        <p id="baslik">Taş Kağıt Makas Oyunu</p>
        
        <div v-if="!oyunBasladi" class="oyun-baslangic">
            <div>
                <label id="tur-sayisi-label" for="tur-sayisi">Tur Sayısı:</label>
                <input type="number" id="tur-sayisi" v-model="tursayisi" min="1" max="10">
            </div>
            <button @click="oyunuBaslat" class="basla-btn" @touchstart="handleTouchStart" @touchend="handleTouchEnd">Oyunu Başlat</button>
        </div>

        <div v-if="oyunBasladi">
            <div id="skor-ve-tur">
                <div id="skor">
                    <p id="Skor">Oyuncu Skoru: {{oyuncuSkor}}</p>
                    <p id="Skor">Bilgisayar Skoru: {{bilgisayarSkor}}</p>
                </div>
                <div>
                    <p id="Tursayisi">Tur: {{tur}} / {{tursayisi}}</p>
                </div>
            </div>
            
            <div v-if="bilgisayarHamle" class="pc-hamle">
                <p>Bilgisayarın hamlesi: {{ bilgisayarHamle }}</p>
            </div>

            <div v-if="oyunDurumu" class="oyun-durumu">
                <p>{{ oyunDurumu }}</p>
            </div>

            <div v-if="oyunSonucu" class="oyun-sonucu">
                <h2>{{ oyunSonucu }}</h2>
            </div>
            
            <div id="oyun" v-if="!oyunBitti">
                <button id="tas" @click="turOyna('Taş')" @touchstart="handleTouchStart" @touchend="handleTouchEnd">TAŞ</button>
                <button id="kagit" @click="turOyna('Kağıt')" @touchstart="handleTouchStart" @touchend="handleTouchEnd">KAĞIT</button>
                <button id="makas" @click="turOyna('Makas')" @touchstart="handleTouchStart" @touchend="handleTouchEnd">MAKAS</button>
            </div>
            
            <div>
                <button id="restart" @click="oyunuYenidenBaslat" @touchstart="handleTouchStart" @touchend="handleTouchEnd">Yeniden Başla</button>
            </div>
        </div>
    </div>
</template>



