<template>
    <header class="header">
        <div class="container">
            <nav class="navbar__container">
                <div class="navbar__container-logo">
                    <img :src="logo" alt="logo" class="navbar__container-logo-img">
                </div>
                <div class="navbar__container-sections">
                    <ul class="navbar__container-sections-ul">
                        <li><a href="#" class="navbar__container-sections-li">Asosiy</a></li>
                        <li><a href="#about" class="navbar__container-sections-li">Biz haqimizda</a></li>
                        <li><a href="#features" class="navbar__container-sections-li">Imkoniyatlar</a></li>
                        <li><a href="#pricing" class="navbar__container-sections-li">Narxlar</a></li>
                    </ul>
                </div>
                <!-- <div class="header__container-logIn">
                    <button class="header__container-logIn-button">Login</button>
                </div> -->
            </nav>
            <div class="header__content">
                <div class="header__content-A">
                    <h2 class="header__content-A-title info">“E-Muhr” elektron hujjat alishish tizimi</h2>
                    <div class="header__content-A-block">
                        <span class="header__content-A-block-text">
                            Hujjatlarni elektron 
                            nazorat qilish
                        </span>
                        <p class="header__content-A-block-description">
                            Elektron hujjat aylanish tizimida hujjatlarni nazorat qilish va ijro nazoratini yo’lga qo’yishingiz mumkin.
                        </p>
                    </div>
                    <UIbutton 
                        label="Bog’lanish"
                        body="Assalomu aleykum, ..."
                        emailLink="main@brb-tech.uz"
                    />
                </div>
                <div class="header__content-B">
                    <img :src="laptop" alt="" class="header__content-B-img">
                </div>
            </div>
        </div>
    </header>
</template>

<script setup>
import logo from '@/assets/img/Logo.svg'
import laptop from '@/assets/img/mockup.svg'
import UIbutton from '@/UI/UIbutton.vue';
</script>

<style lang="scss" scoped>

.header__content{
    margin-top: 120px;
    display: flex;
    align-items: center;
    justify-content: center;
}
.header__content-A{
    display: flex;
    justify-content: center;
    align-items: flex-start;
    flex-direction: column;
    gap: 20px;
    width: 50%;
}
.header__content-A-title{
    width: 305px;
}
.header__content-A-block{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}
.header__content-A-block-text{
    font-size: 80px;
    text-transform: capitalize;
    font-weight: 400;
}
.header__content-A-block-description{
    color: #939393;
    font-size: 16px;
    font-family: SF-Regular;
}
.header__content-A-link{
    padding: 12px 20px;
    border-radius: 12px;
    font-size: 16px;
    background-color: #7A43FA;
    color: #FFFFFF;
}
.header__content-B{
    width: 50%;
}
.header__content-B-img{
 
}


.navbar__container{
    display: flex;
    justify-content: space-between;
    align-content: center;
}
.navbar__container-logo{
    display: flex;
    justify-content: center;
    align-items: center;
}

.navbar__container-sections-li{
    font-size: 22px;
    color: #939393;
    transition: 370ms;
    cursor: pointer;
}
.navbar__container-sections-li:hover{
    color: #424242;
}
.navbar__container-sections{
    
}
.navbar__container-sections-ul{
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 44px;
    padding: 40px 0;
}



//.navbar__container-logIn-button{
//    border-radius: 12px;
//    outline: none;
//    background: black;
//    color: white;
//    height: 48px;
//    width: 80px;
//}
</style>