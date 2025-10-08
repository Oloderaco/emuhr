<template>
  <section id="pricing" class="pricing" ref="sectionEl">
    <div class="container">
      <wrapper class="head">
        <h2 class="head__title">Ta’riflar va Narxlar</h2>
        <p class="head__subtitle">Agar sizga maxsus narxlarda korporativ shartnoma kerak bo’lsa biz bilan bog’laning</p>
        <UIbutton 
          label="Bog’lanish"
          body="Assalomu aleykum, ..."
          emailLink="main@brb-tech.uz"
         />
      </wrapper>

      <div class="grid">
        <article class="card" :class="{ 'is-visible': visible[0] }" :ref="el => (cardRefs[0] = el)">
          <div class="card__body">
            <div class="eyebrow">Sinab ko’rish</div>
            <h3 class="title">Demo</h3>
            <hr class="divider" />
            <ul class="list">
              <li>50 ta hujjatga imzo qo’yish limiti</li>
              <li>2 ta foydalanuvchi (Imzolovchi + 1)</li>
              <li>PDF va Word fayllar bilan ishlash</li>
              <li>Standart imzo moduli</li>
            </ul>
          </div>
            <a
              href="mailto:main@brb-tech.uz?subject=Savol narxlar haqida&body=Assalomu alaykum! Iltimos, ta'riflar haqida ma'lumot bering."
              class="btn tray tray--filled"
            >
              Bog’lanish
            </a>
        </article>

        <article class="card card--featured" :class="{ 'is-visible': visible[1], 'emphasize': emphasizeCenter }" :ref="el => (cardRefs[1] = el)">
          <div class="card__body">
            <div class="eyebrow">Foydalanuvchi soni</div>
            <span class="badge">Mashxur</span>
            <div class="price">
              <span class="price__currency">$</span>
              <span class="price__value">5</span>
            </div>
            <div class="price__meta">/Har bir foydalanuvchi</div>
            <hr class="divider" />
            <ul class="list">
              <li>Barcha Basic funksiyalar</li>
              <li>1 000 ta hujjatgacha imzo chekish</li>
              <li>Role-based imzo bosqichlari</li>
              <li>Ichki notification & log tizimi</li>
              <li>Maxfiylik va shifrlash qoidalari</li>
            </ul>
          </div>
            <a
              href="mailto:main@brb-tech.uz?subject=Savol narxlar haqida&body=Assalomu alaykum! Iltimos, ta'riflar haqida ma'lumot bering."
              class="btn tray tray--filled"
            >
              Bog’lanish
            </a>
          
        </article>

        <article class="card" :class="{ 'is-visible': visible[2] }" :ref="el => (cardRefs[2] = el)">
          <div class="card__body">
            <div class="eyebrow">Kelishilgan narxda</div>
            <h3 class="title">Korporativ</h3>
            <hr class="divider" />
            <ul class="list">
              <li>Barcha Business funksiyalar</li>
              <li>Cheksiz hujjat imzolash</li>
              <li>Cheksiz foydalanuvchi soni</li>
              <li>Shablonlar, avtomatik jarayonlar (workflow)</li>
              <li>Serverga o’rnatiladigan versiya (on-premise)</li>
            </ul>
          </div>
            <a
              href="mailto:main@brb-tech.uz?subject=Savol narxlar haqida&body=Assalomu alaykum! Iltimos, ta'riflar haqida ma'lumot bering."
              class="btn tray tray--filled"
            >
              Bog’lanish
            </a>
        </article>

      </div>
    </div>

  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import UIbutton from '@/UI/UIbutton.vue'

const sectionEl = ref(null)
const cardRefs = ref([])
const visible = ref([false, false, false])
const emphasizeCenter = ref(false)
let started = false

function runSequence() {
  if (started) return
  started = true
  setTimeout(() => (visible.value[0] = true), 60)
  setTimeout(() => (visible.value[2] = true), 300)
  setTimeout(() => {
    visible.value[1] = true
    emphasizeCenter.value = true
    setTimeout(() => (emphasizeCenter.value = false), 700)
  }, 600)
}

onMounted(() => {
  const io = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        runSequence()
        io.disconnect()
      }
    })
  }, { threshold: 0.2 })

  if (sectionEl.value) io.observe(sectionEl.value)
})
</script>

<style scoped>
.pricing { padding: 80px 0 88px; }
.head { display: flex; justify-content: center;
    align-items: center; flex-direction: column; text-align: center; max-width: 860px; margin: 0 auto 80px; }
.head__title { margin: 0 0 8px; font-weight: 700; font-size: 44px; line-height: 1.1; }
.head__subtitle { margin: 0 0 14px; color: #6f6f6f; font-size: 16px; }
.head__cta { margin: 8px auto 0; display: inline-flex; }

.grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 28px; align-items: stretch; }

.card { opacity: 0; transform: translateY(24px) scale(0.98); }
.card.is-visible { opacity: 1; transform: none; transition: opacity .6s ease, transform .6s ease; }

.card.emphasize { animation: pop-in 520ms cubic-bezier(.2,.8,.2,1) both; }
@keyframes pop-in {
  0% { transform: translateY(10px) scale(0.92); opacity: .6; }
  60% { transform: translateY(0) scale(1.04); opacity: 1; }
  100% { transform: translateY(0) scale(1); opacity: 1; }
}

.card {
  position: relative;
  height: 500px;
  background: #ffffff;
  border: 1px solid #eeeeee;
  border-radius: 24px;
  box-shadow: 0 1px 1px rgba(0,0,0,0.02), 0 12px 28px rgba(0,0,0,0.05);
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: column;
  overflow: hidden;
  transition: transform 0.15s ease, box-shadow 0.15s ease;
}
.card:hover { transform: translateY(-2px); box-shadow: 0 16px 36px rgba(0,0,0,0.08); }
.card__body { padding: 28px; position: relative; }
.eyebrow { color: #909090; font-size: 14px; margin-bottom: 8px; }
.title { margin: 0 0 16px; font-weight: 800; font-size: 56px; line-height: 1.06; }
.divider { height: 1px; border: 0; background: #e9e9e9; margin: 18px 0 12px; }

.list { list-style: none; padding: 8px 0 4px; margin: 0; }
.list li {
  display: grid; grid-template-columns: 22px 1fr; align-items: start; gap: 12px;
  padding: 10px 0; color: #1f1f1f; font-size: 18px;
}
.list li::before {
  content: ""; width: 18px; height: 18px; margin-top: 4px; background: #7A43FA;
  -webkit-mask: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12" fill="none" stroke="white" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/></svg>') no-repeat center / contain;
          mask: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><polyline points="20 6 9 17 4 12" fill="none" stroke="white" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/></svg>') no-repeat center / contain;
}

.tray {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  border-top: 1px solid #f1f1f1;
}

.tray--filled {
  background: #7A43FA;
  box-shadow: 0 10px 26px rgba(122,67,250,0.35);
  width: 100%;
}

.card--featured { outline: 2px solid rgba(122,67,250,0.22); box-shadow: 0 14px 34px rgba(122,67,250,0.14), 0 8px 18px rgba(0,0,0,0.06); }
.card--featured .badge { position: absolute; top: 18px; right: 22px; background: rgba(122,67,250,0.14); color: #7A43FA; font-weight: 700; font-size: 12px; padding: 6px 10px; border-radius: 999px; }

.price { display: flex; align-items: baseline; gap: 6px; margin: 4px 0 0; }
.price__currency { font-size: 34px; color: #7A43FA; font-weight: 700; }
.price__value { font-size: 78px; color: #7A43FA; font-weight: 900; line-height: 1; }
.price__meta { color: #7b7b7b; font-size: 14px; margin: 6px 0 10px; }

@media (max-width: 1080px) {
  .grid { grid-template-columns: 1fr; }
  .card { max-width: 760px; margin: 0 auto; }
}

.btn {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  background: #fff;
  color: #1f1f1f;
  font-size: 17px;
  font-weight: 600;
  padding: 20px 0;
  border-radius: 0 0 24px 24px;
  text-decoration: none;
  transition: all 0.25s ease;
  box-shadow: none;
}
.btn:hover {
  background: #7A43FA;
  color: #fff;
  transform: translateY(-1px);
  box-shadow: 0 12px 26px rgba(122,67,250,0.35);
}
</style>