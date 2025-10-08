<template>
  <section id="features" class="features container">
    <h2 class="features__title">Imkoniyatlar</h2>

    <div
      v-for="(feature, index) in features"
      :key="index"
      class="feature"
      :class="{ 'reverse': index % 2 !== 0 }"
    >
      <div class="feature__image">
        <img :src="feature.image" :alt="feature.title" />
      </div>

      <div class="feature__content">
        <h3 class="feature__title">{{ feature.title }}</h3>
        <p class="feature__text">{{ feature.text }}</p>
      </div>
    </div>
  </section>
</template>

<script setup>
import brain from '@/assets/img/brain.jpg'
import clock from '@/assets/img/clock.jpg'
import lock from '@/assets/img/lock.jpg'
import messages from '@/assets/img/messages.jpg'
const features = [
  {
    title: "Hujjatlar tartibli saqlanishi",
    text: "Har bir hujjat yagona markazda saqlanadi. Kategoriya, loyiha yoki bo‘lim bo‘yicha avtomatik tartiblanadi. Qidiruv tizimi va filtrlar yordamida kerakli faylni soniyalar ichida topish mumkin.",
    image: messages,
  },
  {
    title: "Real-time hujjat aylanish imkoniyati",
    text: "Hujjatlar tasdiqlash, imzolash va jo‘natish jarayoni real vaqt rejimida amalga oshadi. Tizim har bir harakatni kuzatib boradi va barcha o‘zgarishlarni avtomatik tarzda yangilaydi.",
    image: clock,
  },
  {
    title: "Tizimni markaziy boshqaruvi",
    text: "Administratorlar barcha jarayonlarni bitta boshqaruv paneli orqali nazorat qiladi. Rollar, ruxsatlar va foydalanuvchi faoliyatini tahlil qilish tizimni yanada shaffof qiladi.",
    image: brain,
  },
  {
    title: "Hujjat va ma’lumotlar xavfsizligi",
    text: "Ma’lumotlar ko‘p bosqichli shifrlash bilan himoyalanadi. Har bir foydalanuvchi uchun maxsus autentifikatsiya qo‘llaniladi, bu esa tizimni xavfsiz va barqaror qiladi.",
    image: lock,
  },
];
</script>

<style lang="scss" scoped>
.features__title {
  font-size: 48px;
  font-weight: 700;
  text-align: center;
  margin-bottom: 48px;
  margin: 80px 0;
}

.feature {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 48px;
  margin-bottom: 120px;

  &.reverse {
    flex-direction: row-reverse;
  }
}

.feature__image {
  //flex: 1 1 480px;
  display: flex;
  //justify-content: center;
  //align-items: center;
  

  img {
    width: 100%;
    max-width: 420px;
    border-radius: 20px;
    display: block;
  }
}

.feature__content {
  flex: 1 1 520px;
  min-width: 320px;
  max-width: 560px;
  text-align: left;
}

.feature__title {
  font-size: clamp(22px, 2.6vw, 34px);
  font-weight: 500;
  line-height: 1.15;
  margin: 0 0 12px;
  position: relative;
  padding-left: 14px;
}

.feature__title::before {
  content: "";
  position: absolute;
  left: 0;
  top: 2px;
  bottom: 2px;
  width: 3px;
  background: hsl(var(--primary, 270 90% 55%));
  border-radius: 2px;
}

.feature__text {
  font-size: 18px;
  color: #939393;
  line-height: 1.6;
  max-width: 420px;     
  white-space: normal;
  word-break: normal;
}

@media (max-width: 900px) {
  .feature {
    flex-direction: column;
    text-align: center;
    gap: 28px;
    margin-bottom: 72px;
  }
  .feature.reverse { flex-direction: column; }
  .feature__title::before { display: none; }
  .feature__content { min-width: 0; max-width: 640px; text-align: center; }
  .feature__text { margin: 0 auto; }
}
</style>