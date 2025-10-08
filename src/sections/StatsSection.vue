<template>
  <section class="wrapper container">
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
          {{ s.value }}
        </div>
        <div class="wrapper__label">{{ s.label }}</div>
      </div>
    </div>
  </section>
</template>

<script setup>
const items = [
  { value: '50+',     label: 'Foydalanuvchilar' },
  { value: '500+',    label: 'Hujjat almashinuvi' },
  { value: '4.9/5.0', label: 'Berilgan baholar' },
  { value: '3x',      label: 'Vaqtni tejash' },
];
</script>

<style lang="scss" scoped>
:root { --primary: 270 90% 55%; } /* если уже объявлен глобально — удали эту строку */

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
  display: flex;                 /* FLEX вместо GRID */
  flex-wrap: wrap;               /* перенос строк */
  justify-content: space-between;/* равные промежутки между карточками */
  row-gap: clamp(16px, 3vw, 32px);/* вертикальный промежуток между рядами */
  column-gap: 0;                 /* горизонтальный gap не нужен при space-between */
  border-top: 2px solid hsl(var(--primary) / .6);
  border-bottom: 2px solid hsl(var(--primary) / .6);
  padding: 28px 0;
}
.wrapper__item {
  flex: 0 1 220px;      /* базовая ширина карточки; помещается 4 шт на десктопе */
  display: flex;
  flex-direction: column;
  align-items: center;  /* центр содержимого */
  text-align: center;   /* центр текста */
}

.wrapper__value {
  font-size: clamp(36px, 5vw, 72px);
  font-weight: 700;
  color: #000;
  line-height: 1;
  display: inline-block;
  position: relative;
}
/* solid purple underline under first number */
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