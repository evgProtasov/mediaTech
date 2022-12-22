<script>
export default {

}
</script>

<template>
    <div class="products-container">
        <div class="products">
            <div class="products-info">
                <p><span class="products-info__main">Главная</span>><span class="products-info__submain">Продукция</span></p>
            </div>
            <div class="products-list">
                <div class="products-list__title">
                    <h2>Продукция</h2>
                </div>
                <div class="products-list__container">
                    <div class="products-item">
                        <div class="products-item__name">
                            Курьерские пакеты с карманом
                        </div>
                        <div class="products-item__img">
                            <img src="../img/icons/packwithpocket1.png" alt="packwithpockets">
                        </div>
                        <div class="products-item__price">
                            <span>от 5.90 ₽ / шт</span>                            
                        </div>
                    </div>
                    <div class="products-item">
                        <div class="products-item__name">
                            Пакеты Дой-Пак (Doy Pack)
                        </div>
                        <div class="products-item__img">
                            <img src="../img/icons/packdaypak1.png" alt="packdoypak">
                        </div>
                        <div class="products-item__price">
                            <span>от 0.50 ₽ / шт</span>                            
                        </div>
                    </div>
                    <div class="products-item">
                        <div class="products-item__name">
                            Курьерские пакеты без кармана
                        </div>
                        <div class="products-item__img">
                            <img src="../img/icons/packwithpocket1.png" alt="packwithpockets">
                        </div>
                        <div class="products-item__price">
                            <span>от 4.75 ₽ / шт</span>                            
                        </div>
                    </div>
                    <div class="products-item">
                        <div class="products-item__name">
                            Крафт пакеты дой-пак с прозрачным окном
                        </div>
                        <div class="products-item__img">
                            <img src="../img/icons/craftdoypack1.png" alt="craftdoypack">
                        </div>
                        <div class="products-item__price">
                            <span>от 0.50 ₽ / шт</span>                            
                        </div>
                    </div>
                    <div class="products-item">
                        <div class="products-item__name">
                            Полипропиленовые пакеты
                        </div>
                        <div class="products-item__img">
                            <img src="../img/icons/polypropilen1.png" alt="polypropilen">
                        </div>
                        <div class="products-item__price">
                            <span>от 0.85 ₽ / шт</span>                            
                        </div>
                    </div>
                    <div class="products-item">
                        <div class="products-item__name">
                            БОПП пакеты
                        </div>
                        <div class="products-item__img">
                            <img src="../img/icons/bopp1.png" alt="bopp">
                        </div>
                        <div class="products-item__price">
                            <span>от 0.40 ₽ / шт</span>                            
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.products-container {
    max-width: 1260px;
    margin: 0 auto;
}
.products {
    margin-top: 56px;
}
.products-info {
    font-size: 12px;
    color: #9CABB9;
}
.products-info__main {
    color: #142637;
    padding-right: 8.75px;
}
.products-info__submain {
    padding-left: 8.75px;
}
.products-list {
    margin-top: 8px;
}
.products-list h2 {
    font-size: 40px;
    line-height: 48px;
}
.products-list__container {
    margin-top: 32px;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-gap: 8px;
}
.products-item {
    /* max-width: 309px; */
    background: #F5F7FA;
    border-radius: 20px;
    padding: 24px;
    cursor: pointer;
    transition: all 0.5s ease;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}
.products-item:hover {
    transform: translateY(-10px);
    
}
.products-item__name {
    font-size: 20px;
    line-height: 28px;
    font-weight: 500;
    /* height: 56px; */
}
.products-item__img {
    margin-top: 12px;
}
.products-item__img img {
    width: 100%;
    height: 100%;
}
.products-item__price {
    
    margin-top: 12px;     
}
.products-item__price span {
    padding: 8px 16px;
    background: #FFFFFF;
    border-radius: 8px;
    cursor: pointer;
}

@media (max-width: 1280px) {
    .products {
        margin: 0px 24px;
        margin-top: 40px;
    }
    .products-list__container {
        margin-top: 24px;
        max-width: 1216px;
    }
    .products-item {
       max-width: 298px;
    }
    .products-list h2 {
        font-size: 32px;
        line-height: 40px;
    }
}

@media (max-width: 1260px) {
    .products-list__container {
        grid-template-columns: repeat(4, minmax(200px, 1fr));
    }
    .products-item {
        max-width: 309px;
    }
}
@media (max-width: 1024px) {
    .products-list__container {
        grid-template-columns: repeat(3, minmax(200px, 1fr));
    }
    .products {
        margin: 40px 32px 0px;
    }
}
@media (max-width: 768px) {
    .products-list__container {
        grid-template-columns: repeat(2, minmax(200px, 1fr));
    }
}
@media (max-width: 510px) {
    .products-list__container {
        grid-template-columns: minmax(200px, 1fr);
    }
    .products {
        margin: 20px 20px 0px;
    }
    .products-list h2 {
        font-size: 24px;
        line-height: 32px;
    }
    .products-item {
        max-width: 335px;
    }
    
}
</style>