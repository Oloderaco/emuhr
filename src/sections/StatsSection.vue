<template>
  <section class="wrapper container" ref="sectionEl">
    <div class="wrapper__blocks">
      <div class="wrapper__block-A">
        <span id="about" class="wrapper__block-A-span info">Biz haqimizda</span>
        <h2 class="wrapper__block-A-text">
          Bizning<br />
          ko’rsatkichlarimiz
        </h2>
      </div>

      <div class="wrapper__block-B">
        <span class="hl">Ushbu tizim yordamida ish jarayonlari</span>
        <span class="hl">tezligini bir necha barobarga</span>
        <span class="hl">tezlashtirish imkoni mavjud</span>
      </div>
    </div>

    <div class="wrapper__grid">
      <div class="wrapper__item" v-for="(s, i) in items" :key="i">
        <div class="wrapper__value" :class="{ 'with-underline': i === 0 }">
          {{ formatValue(displayValues[i], s.decimals) }}{{ s.suffix }}
        </div>
        <div class="wrapper__label">{{ s.label }}</div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

// Explicit targets and suffixes so мы красиво форматируем
const items = [
  { target: 50,   suffix: '+',   label: 'Foydalanuvchilar',   decimals: 0 },
  { target: 500,  suffix: '+',   label: 'Hujjat almashinuvi', decimals: 0 },
  { target: 4.9,  suffix: '/5.0',label: 'Berilgan baholar',   decimals: 1 },
  { target: 3,    suffix: 'x',   label: 'Vaqtni tejash',      decimals: 0 },
]

// Отрисовываемые значения (стартуют с нуля)
const displayValues = ref(items.map(() => 0))

// Реф на секцию, чтобы запустить анимацию при появлении
const sectionEl = ref(null)
let started = false

const DURATION = 1500 // ms

const easeOutCubic = (t) => 1 - Math.pow(1 - t, 3)

function animateCount() {
  const start = performance.now()
  const from = displayValues.value.slice()

  function frame(now) {
    const progress = Math.min(1, (now - start) / DURATION)
    const eased = easeOutCubic(progress)

    displayValues.value = items.map((it, idx) => {
      const startVal = from[idx] || 0
      const delta = it.target - startVal
      return startVal + delta * eased
    })

    // Если это последний элемент (3x), включаем эффект увеличения
    if (progress < 1 && items[3]) {
      const el = document.querySelector('.wrapper__item:nth-child(4) .wrapper__value')
      if (el) {
        el.style.transform = `scale(${1 + 0.2 * Math.sin(progress * Math.PI)})`
      }
    } else {
      const el = document.querySelector('.wrapper__item:nth-child(4) .wrapper__value')
      if (el) el.style.transform = 'scale(1)'
    }

    if (progress < 1) requestAnimationFrame(frame)
    else {
      // На всякий случай зафиксируем точные целевые значения
      displayValues.value = items.map((it) => it.target)
    }
  }

  requestAnimationFrame(frame)
}

function formatValue(v, decimals = 0) {
  // аккуратно форматируем с нужным количеством знаков после запятой
  return Number(v).toFixed(decimals).replace(/\.0+$/, '')
}

onMounted(() => {
  // Запуск при появлении секции на экране
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting && !started) {
        started = true
        animateCount()
        observer.disconnect()
      }
    })
  }, { threshold: 0.25 })

  if (sectionEl.value) observer.observe(sectionEl.value)
})
</script>

<style lang="scss" scoped>
:root { --primary: 270 90% 55%; }

.wrapper { 
    padding: 64px 0 48px; 
    margin-top: 100px;
}

.wrapper__blocks {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 50px;
  margin-bottom: 40px;
}

.wrapper__block-A{
    display: flex;
    justify-content: center;
    align-items: flex-start;
    flex-direction: column;
    gap: 16px;
}
.wrapper__block-A-span {
font-size: 16px;
}
.wrapper__block-A-text {
  font-weight: 400;
  margin: 0;
  font-size: clamp(28px, 3.2vw, 40px);
  line-height: 1.1;
}

.wrapper__block-B {
  display: flex;
  justify-content: center;
  align-items: flex-end;
  flex-direction: column;
}
.wrapper__block-B .hl {
  display: block;
  position: relative;
  margin: 6px 0;
  padding-bottom: 6px;
  font-weight: 500;
  font-size: 28px;
}
.wrapper__block-B .hl::after {
  content: "";
  position: absolute;
  left: 0; right: 0; bottom: 0;
  height: 4px;
  background: hsl(var(--primary));
  transform: translateY(2px);
}

.wrapper__grid {
  margin-top: clamp(24px, 4vw, 48px);
  display: flex;                 
  flex-wrap: wrap;               
  justify-content: space-between;
  row-gap: clamp(16px, 3vw, 32px);
  column-gap: 0;                 
  border-top: 2px solid hsl(var(--primary) / .6);
  border-bottom: 2px solid hsl(var(--primary) / .6);
  padding: 28px 0;
}
.wrapper__item {
  flex: 0 1 220px;     
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;  
}

.wrapper__value {
  font-size: clamp(36px, 5vw, 72px);
  font-weight: 700;
  color: #000;
  line-height: 1;
  display: inline-block;
  position: relative;
  transition: transform 0.3s ease;
}

.wrapper__value.with-underline::after {
  content: "";
  position: absolute;
  bottom: -6px;
  left: 0;
  width: 60%;
  height: 3px;
  background: hsl(var(--primary));
}

.wrapper__label {
  margin-top: 12px;
  color: #9b9b9b;
  font-size: 16px;
}

@media (max-width: 1024px) {
  .wrapper__blocks { grid-template-columns: 1fr; }
  .wrapper__block-B { font-size: clamp(28px, 6vw, 48px); }
}
@media (max-width: 720px) {
  .wrapper__grid { justify-content: center; }
  .wrapper__item { flex: 0 1 45%; }
}
@media (max-width: 460px) {
  .wrapper__item { flex: 0 1 100%; }
}
</style>