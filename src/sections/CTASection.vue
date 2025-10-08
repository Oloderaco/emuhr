<template>
    <div class="wrapper">
        <div class="container">
            <div class="pricing__ad">
            <h2 class="pricing__ad-title">Muammolarni yechimini ortga surmang!</h2>
            <div class="pricing__ad-box">
                <span class="pricing__ad-box-text">Tashkilotingiz uchun ijro nazorati va hujjatlar aylanmasini elektron shaklda olib borish uchun eng optimal yechim. Batafsil ma’lumot uchun va bepul konsultatsiya uchun biz bilan bog’laning</span>
                <UIbutton 
                label="bog'lanish" 
                bgColor="#F5F5F5" 
                textColor="black"
                body="Здравствуйте! Подскажите, пожалуйста..."
                emailLink="main@brb-tech.uz"
                />
            </div>
        </div>
        </div>
    </div>
</template>

<script setup>
import UIbutton from '@/UI/UIbutton.vue';
</script>

<style lang="scss" scoped>

.pricing__ad{
    display: flex;
    justify-content: space-between;
    align-items: center;
background: radial-gradient(
  70% 120% at 30% 40%, 
  #4B2DCC 0%, 
  #2E1E60 35%, 
  #1A141F 70%, 
  #0C0A0C 100%
);
    border-radius: 32px;
    padding: 0 60px;


}
.pricing__ad-title{
    width: 420px;
    font-weight: 500;
    font-size: 54px;
    color: #FFFFFF;
}
.pricing__ad-box{
    display: flex;
    justify-content: center;
    align-items: flex-start;
    flex-direction: column;
    width: 400px;
    gap: 25px;
}
.pricing__ad-box-text{
    font-size: 16px;
    line-height: 24px;
    font-weight: 400;
    color: #FFFFFF;
}
</style>