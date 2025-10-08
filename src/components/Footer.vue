<template>
    <footer class="footer">
        <div class="container">
            <div class="footer__container">
                <ul class="footer__container-ul">
                    <a href="#about" class="footer__container-ul-list">
                        Biz haqimizda
                    </a>
                    <a href="#features" class="footer__container-ul-list">
                        Imkoniyatlar
                    </a>
                    <a href="#pricing" class="footer__container-ul-list">
                        Narxlar
                    </a>
                    <a href="#" class="footer__container-ul-list">
                        Elektron hujjat aylanish tizimi
                    </a>
                </ul>
                <div class="footer__container-box">
                    <ul class="footer__container-box-links">
                        <a
                          href="https://www.instagram.com/brbtech.uz/"
                          target="_blank"
                          rel="noopener noreferrer"
                          class="footer__container-box-link"
                        >
                            <img :src="instagram" alt="" class="footer__img">
                        </a>
                        <a
                          href="https://www.linkedin.com/company/brb-tech/"
                          target="_blank"
                          rel="noopener noreferrer"
                          class="footer__container-box-link"
                        >
                            <img :src="linked" alt="" class="footer__img">
                        </a>
                        <a
                          href="https://www.facebook.com/brbtech.uz"
                          target="_blank"
                          rel="noopener noreferrer"
                          class="footer__container-box-link"
                        >
                            <img :src="facebook" alt="" class="footer__img">
                        </a>
                        <a
                          href="https://t.me/brbtech"
                          target="_blank"
                          rel="noopener noreferrer"
                          class="footer__container-box-link"
                        >
                            <img :src="telegram" alt="" class="footer__img">
                        </a>   
                    </ul>
                    <span class="footer__container-box-text">
                        Bizni ijtimoiy tarmoqlarda kuzating
                    </span>
                    <a href="tel:+998555130505" class="footer__container-box-text">
                        +998 (55) 513 05 05
                    </a>
                    <span class="footer__container-box-rights">
                        © 2025 All RIghts Reserved
                    </span>
                </div>
            </div>
        </div>
    </footer>
</template>

<script setup>
import telegram from '@/assets/img/telegram.svg'
import linked from '@/assets/img/in.svg'
import facebook from '@/assets/img/facebook.svg'
import instagram from '@/assets/img/instagram.svg'
</script>

<style lang="scss" scoped>
.footer{
    margin-top: 64px;
    background: #111111;
    padding: 50px;
}
.footer__container{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 250px;

}
.footer__container-box-links{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 15px;
}
.footer__container-ul{
    display: flex;
    justify-content: center;
    align-items: flex-start;
    gap: 25px;
    flex-direction: column;

}
.footer__container-ul-list{
    color: white;
}
.footer__container-box{
    display: flex;
    justify-content: center;
    align-items: flex-end;
    flex-direction: column;
    gap: 30px;
}
.footer__container-box-text{
    font-size: 12px;
    line-height: 18px;
    color :white;
    letter-spacing: -1%;
}
.footer__container-box-rights{
    line-height: 20px;
    font-size: 14px;
    font-weight: 400;
    color: #FFFFFF;
}

</style>