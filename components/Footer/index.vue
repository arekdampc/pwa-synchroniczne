<template>
    <footer class="footer">
        <div class="footer_section">
            <div class ="footer_hyperlinks">
                <div class ="first_column">
                    <h3>Zamowienia</h3>
                    <ul class="zamowienia">
                        <li @click="handleClickZamowienia"><a href="#">Dostawa</a></li>
                        <li @click="handleClickZamowienia"><a href="#">Raty</a></li>
                        <li @click="handleClickZamowienia"><a href="#">Leasing</a></li>
                        <li @click="handleClickZamowienia"><a href="#">Ubezpieczenia</a></li>
                        <li @click="handleClickZamowienia"><a href="#">TaxFree</a></li>
                        <li @click="handleClickZamowienia"><a href="#">Montaz</a></li>
                        <li @click="handleClickZamowienia"><a href="#">Zwroty i reklamacje</a></li>
                        <li @click="handleClickZamowienia"><a href="#">Najczesciej zadawane pytania</a></li>
                    </ul>
                </div>
                <div class ="second_column">
                    <h3>Promocje i inspiracje</h3>
                    <ul class="promocje">
                        <li @click="handleClickPromocje"><a href="#">Wyprzedaz</a></li>
                        <li @click="handleClickPromocje"><a href="#">Goracy strzal</a></li>
                        <li @click="handleClickPromocje"><a href="#">un.Box</a></li>
                        <li @click="handleClickPromocje"><a href="#">Promocje</a></li>
                        <li @click="handleClickPromocje"><a href="#">Karty podarunkowe</a></li>
                        <li @click="handleClickPromocje"><a href="#">Poradniki</a></li>
                        <li @click="handleClickPromocje"><a href="#">Aktualnosci</a></li>
                    </ul>
                </div>
                <div class ="third_column">
                    <h3>x-kom</h3>
                    <ul class="x-kom">
                        <li @click="handleClickxkom"><a href="#">O nas</a></li>
                        <li @click="handleClickxkom"><a href="#">Regulamin</a></li>
                        <li @click="handleClickxkom"><a href="#">Polityka prywatnosci</a></li>
                        <li @click="handleClickxkom"><a href="#">Polityka cookies</a></li>
                        <li @click="handleClickxkom"><a href="#">Regulamin newslettera</a></li>
                        <li @click="handleClickxkom"><a href="#">Biuro prasowe</a></li>
                        <li @click="handleClickxkom"><a href="#">Zamowienia publiczne</a></li>
                        <li @click="handleClickxkom"><a href="#">Zakupy dla firm</a></li>
                        <li @click="handleClickxkom"><a href="#">Wspolpraca marketingowa</a></li>
                        <li @click="handleClickxkom"><a href="#">Geex</a></li>
                        <li @click="handleClickxkom"><a href="#">Forum</a></li>
                        <li @click="handleClickxkom"><a href="#">Kariera</a></li>
                        <li @click="handleClickxkom"><a href="#">Kontakt</a></li>
                        <li @click="hanhandleClickxkomdleClick"><a href="#">Realizowane projekty</a></li>
                    </ul>
                </div>
            </div>
            <div class="contact">
                <div class="contact_info">
                    <h3>Kontakt</h3>
                    <p>Telefon: 123 456 789</p>
                    <p>Email:</p>
                    <div class="social_media">
                        <a href="#"><img src="https://cdn.iconscout.com/icon/free/png-512/free-facebook-1664126-1412949.png" alt="facebook"></a>
                        <a href="#"><img src="https://cdn.iconscout.com/icon/free/png-256/instagram-233-896451.png" alt="instagram"></a>
                        <a href="#"><img src="https://cdn.iconscout.com/icon/free/png-256/twitter-1867541-1583140.png" alt="twitter"></a>
                        <a href="#"><img src="https://cdn.iconscout.com/icon/free/png-512/free-twitter-9420782-7651212.png" alt="twitter"></a>
                    </div>
                </div>
            </div>
        </div>
        <div class="payments">
            <div class="payments_images">
                <img src="/public/footer/inpost.png" alt="inpost">
                <img src="/public/footer/ups.png" alt="ups">
                <img src="/public/footer/fedex.png" alt="fedex">
                <img src="/public/footer/dts.png" alt="dts">
                <img src="/public/footer/poczta_polska.png" alt="poczta_polska">
                <img src="/public/footer/przelewy24.png" alt="przelewy24">
                <img src="/public/footer/blik.png" alt="blik">
                <img src="/public/footer/mastercard.png" alt="mastercard">
                <img src="/public/footer/visa.png" alt="visa">
                <img src="/public/footer/pko.png" alt="pko">
                <img src="/public/footer/grenke.png" alt="grenke">
                <img src="/public/footer/santander.png" alt="santander">
                <img src="/public/footer/alior.png" alt="alior_bank">
                <img src="/public/footer/allianz.png" alt="allianz">
            </div>
        </div>
        <div class="footer_info">
            <p>Arkadiusz Dampc, Damian Gorski, Julia Korzeniewska, Andrzej Milewczyk, Mariusz Gwara</p>
        </div>
    </footer>
</template>

<script>
export default {
    methods: {
        handleClickZamowienia() {
            console.log('Link from zamowienia section clicked');
        },
        handleClickPromocje() {
            console.log('Link from promocje section clicked');
        },
        handleClickxkom() {
            console.log('Link from x-kom section clicked');
        }
    }
}
</script>

<style lang="scss" scoped>
@import './footer.scss';
@import url('https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,100;0,300;0,400;0,700;0,900;1,100;1,300;1,400;1,700;1,900&display=swap');
</style>
