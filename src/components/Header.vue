<script>
export default {
    data() {
        return {
            isHover: false,
            isModal: false,
            cities: [
                {id: 1, youCity: 'Киров'},
                {id: 2, youCity: 'Москва'},
                {id: 3, youCity: 'Екатеринбург'},
                {id: 4, youCity: 'Краснодар'},
                {id: 5, youCity: 'Нижний Новгород'},
                {id: 6, youCity: 'Новосибирск'},
                {id: 7, youCity: 'Ростов-на-Дону'},
                {id: 8, youCity: 'Самара'},
                {id: 9, youCity: 'Санкт-Петербург'},
                {id: 10, youCity: 'Уфа'},
                {id: 11, youCity: 'Челябинск'},
            ],
            currentCity: '',
            yourCity: ''
        }
    },
    methods: {
        setHover() {
            this.isHover = !this.isHover
        },
        setModal() {
            this.isModal = !this.isModal
            
        }
    },
    computed: {
        filteredCities() {
            let city = this.yourCity;
            return this.cities.filter(function(elem) {
                if (city === '') return true;
                else return elem.youCity.indexOf(city) > -1
            })
        }
    }
}
</script>

<template>
    <div class="header-nav">        
            <div class="header-nav__top">
                <div class="header-nav__container">
                    <div class="top-city" >
                        <span @click="setModal()">{{ (currentCity != '') ? currentCity.youCity : 'Ваш город' }}</span>
                    </div>
                    <div class="top-mobile" @click="setModal()">
                        <img src="../img/icons/header-icon.svg" alt="">
                    </div>
                </div>                
            </div>  
            <div class="header-nav__bottom">
                <div class="header-nav__container">
                    <nav class="bottom-menu">
                        <div class="bottom-menu__icon">
                                <a href="#" class="icon__link">
                                    <img src="../img/icons/logo.svg" alt="logo">
                                </a>                         
                        </div>
                        <div class="bottom-menu__list">                            
                            
                            <div class="bottom-menu__item" @click="setHover()">
                                <div class="bottom-menu__item_list" :class="{active: isHover}">
                                    <a href="#">Продукция</a>
                                </div>                               
                                
                                <div class="bottom-menu__submenu" v-show="isHover">
                                    <div class="submenu-list">
                                        <div class="submenu-item">
                                            <a href="#">Курьерские пакеты с карманом</a>
                                        </div>
                                        <div class="submenu-item">
                                            <a href="#">Пакеты Дой-Пак (Doy Pack)</a>
                                        </div>
                                        <div class="submenu-item">
                                            <a href="#">Курьерские пакеты без кармана</a>
                                        </div>
                                        <div class="submenu-item">
                                            <a href="#">Крафт пакеты дой-пак с прозрачным окном</a>
                                        </div>
                                        <div class="submenu-item">
                                            <a href="#">Полипропиленовые пакеты</a>
                                        </div>
                                        <div class="submenu-item">
                                            <a href="#">БОПП пакеты</a>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            <div class="bottom-menu__item">
                                <a href="#">Доставка и оплата</a>
                            </div>
                            <div class="bottom-menu__item">
                                <a href="#">Отзывы</a>
                            </div>
                            <div class="bottom-menu__item">
                                <a href="#">Заказчики</a>
                            </div>
                            <div class="bottom-menu__item">
                                <a href="#">О компании</a>
                            </div>
                            <div class="bottom-menu__item">
                                <a href="#">Контакты</a>
                            </div>
                        </div>                        
                        <div class="bottom-menu__phone">
                            <a href="tel:+78004567500">8 800 456-75-00</a>
                        </div>
                    </nav>
                </div>
            </div>
        <div class="modal" v-if="isModal">
            <div class="modal__container">
                <div class="modal__close" @click="setModal()">

                </div>
                <div class="modal__name">
                    Выберите город
                </div>
                <div class="modal__input">
                    <input type="text" placeholder="Ваш город" v-model="yourCity">
                </div>                
                <div class="modal__search">
                    Определить автоматически
                </div>
                <div class="modal__radio">
                    <label class="radio__label" v-for="city in filteredCities" :key="city.id">
                        <input class="radio__input" type="radio" :value="city" name="city" v-model="currentCity">
                        <span class="radio__box"></span>
                        {{city.youCity}}
                    </label>                    
                </div>
            </div>
        </div>        
    </div>        
    
</template>

<style scoped>
/* Modal */
.modal {
    /* height: 100vh;
    width: 100vw; */
    position: fixed;
    background: #9cabb9d8;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
}
.modal__container {
    display: flex;
    flex-direction: column;
    max-width: 480px;
    padding: 16px 48px 48px;
    background: #FFFFFF;
    border-radius: 25px;
}
.modal__close {
    background: url('../img/icons/modal-close.svg') no-repeat;
    height: 32px;
    width: 32px;
    display: flex;
    align-self: flex-end;
    cursor: pointer;
}
.modal__name {
    font-size: 40px;
    line-height: 48px
}
.modal__input {
    max-width: 352px;
    display: flex;
    align-items: center;
    padding-bottom: 12px;
    border-bottom: 1px solid rgba(20, 38, 55, 0.12);
}
.modal__input::after {
    content: url('../img/icons/search.svg');
    width: 17px;
    height: 17px;
    align-self: flex-end;
    cursor: pointer;
}
.modal__input input {
    margin-top: 24px;
    outline: none;
    border: none;
    height: 24px;
    color: #83909D;
    font-size: 18px;
    line-height: 24px;
    width: 100%;
}
.modal__search {
    margin-top: 22px;
    font-size: 14px;
    line-height: 20px;
    font-weight: 500;
    text-align: center;
    border: 1px solid rgba(20, 38, 55, 0.12);
    border-radius: 24px;
    padding: 10px 0px;
    cursor: pointer;
}
.modal__search::before {
    content: url('../img/icons/modal-search-auto.svg');
    padding-right: 6px;
    padding-top: 2px;
}
.modal__radio {
    margin-top: 24px;
    display: flex;
    flex-direction: column;
    gap: 12px;
}
.radio__label {
    position: relative;
    display: flex;
    justify-content: space-between;
    flex-direction: row-reverse;
    cursor: pointer;
}
.radio__input {
  /* position: absolute; */
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}
.radio__input:checked + .radio__box {
  background-image: url("../img/icons/radio-cheched.svg");
  background-repeat: no-repeat;
}
.radio__box {
  position: absolute;
  width: 20px;
  height: 20px;
  background-image: url("../img/icons/radio-unchecked.svg");
  margin-left: -30px;
  top: 0;
  background-repeat: no-repeat;
}
/* -------------------------------------------------------------------- */
.active {
    background: #DC223E !important;
    color: #FFFFFF;
}
.header-nav__container {
    max-width: 1260px;
    margin: 0 auto;    
}
.header-nav {    
    background-color: #F5F7FA;
    border-radius: 16px;
    margin-top: 8px;
}
.header-nav__top {
    border-bottom: 1px solid  rgba(20, 38, 55, 0.08);
}
.header-nav__bottom {
    padding: 24px 0;
}
.top-mobile {
    display: none;
}
.top-city {
    font-weight: 400;
    font-size: 14px;
    line-height: 20px;
    padding: 12px 0 12px 0;
    display: flex;
    align-self: center;
}
.top-city span {
    cursor: pointer;
    display: flex;
    align-items: center;
}
.top-city span:hover {
    color: #DC223E;
}
.top-city span::before {
    content: url('../img/icons/header-icon.svg');
    width: 16px;
    height: 16px;
    padding-right: 6px;
}
.bottom-menu {
    display: flex;    
}
.bottom-menu__list {
    list-style: none;
    line-height: 24px;
    display: flex;
    align-items: center;
    gap: 24px;
    margin-right: 109px;
}
.bottom-menu__item:first-child:hover .bottom-menu__item_list::after {
    content: url('../img/icons/products-active.svg');
}
.bottom-menu__submenu {
    position: absolute;
    background: #FFFFFF;
    box-shadow: 0px 4px 16px rgba(20, 38, 55, 0.04);
    border-radius: 12px;
    top: 130px;
    color: #142637;
     
}
.submenu-list {
    padding: 24px 32px;
    font-size: 16px;
    line-height: 24px;
    display: flex;
    flex-direction: column;
    gap: 20px;
}
.submenu-item:hover {
    color: #DC223E;
}
.bottom-menu__item_list {
    padding: 8px 18px 8px 16px;
    background: #FFFFFF;
    border-radius: 8px;   
}
.bottom-menu__item_list::after {
    content: url('../img/icons/products.svg');
    width: 7.5px;
    height: 4.5px;
    padding-left: 8px;
}
.bottom-menu__item_list:hover {
    background: #DC223E;
    color: #FFFFFF;
    cursor: pointer;
}
/* .bottom-menu__item_list:hover::after{
    content: url('../img/icons/products-active.svg');
} */
.bottom-menu__item:not(:first-child):hover {
    color: #DC223E;
}
.bottom-menu__icon {
    margin-right: 36px;
}
.bottom-menu__phone {
    font-weight: 500;
    font-size: 20px;
    line-height: 28px;
    align-self: center;
}
.bottom-menu__phone:hover {
    color: #DC223E;
}

@media (max-width: 1280px) {
    .header-nav__container {
        padding-left: 26px;
    }
    .bottom-menu__list {
        margin-right: 65px;
    }
    
}

@media (max-width: 1260px) {
    .header-nav__top {
        border: none;
        display: flex;
        order: 2;
        align-self: center;
    }
    .bottom-menu__list {
        display: none;
    }
    .bottom-menu__phone {
        display: none;
    }
    .header-nav {
        display: flex;
        align-self: center;
        padding: 12px 40px;
        justify-content: space-between;
    }
    .header-nav__bottom {
        padding: 0;
        display: flex;
        order: 1;
    }
    .header-nav__container {
        padding: 0;
    }
    .top-city {
        padding: 0;
    }
    .top-city span {
        display: none;
    }
    .top-mobile {
        display: block;
        border: 1px solid #9CABB9;
        border-radius: 50%;
        position: relative;
        font-size: 0;
    }
    .bottom-menu__icon {
        margin-right: 0;
    }
    .top-mobile img {
        padding: 5px;
        
    }
    .icon__link img {
        height: 36px;
    }
    
}

@media (max-width: 580px) {
    .header-nav {
        margin-top: 0;
        border-radius: 0;
        padding: 23px 20px;
    }
}
@media (max-width: 375px) {
    .icon__link img {
        height: 30px;
    }
}
</style>