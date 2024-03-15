<script setup>
import Slider from './components/Slider.vue';
import Tab from './components/Tab.vue';
</script>
<template>
  <main>
    <section class="tovar">
      <nav class="slider">
        <Slider />
      </nav>
      <nav class="tovar_items">
        <div class="tovar_item">
          <h1 class="tovar_name">
            Business Gaming V2 PC | AMD Ryzen 5 4500 | GTX 1050 Ti 4GB | 16GB RAM | 1000GB M.2 SSD | WildRabbit Aero RGB | Win 11 | WiFi | Libre Open Office
          </h1>
          <ul>
            <li>Intel Core i3-10105 4x 3.70-4.40GHz</li>
            <li>Mainboard Markenname Bezeichnung XXXX</li>
            <li>Grafikkarte GPU Takt</li>
            <li>Arbeitsspeicher XXGB RAM</li>
            <li>Festplatte No.1 XGB SSD</li>
            <li>Festplatte No.2 XGB SSD</li>
            <li>Festplatte XGB HHD refurbished</li>
            <li>DVD Writer Marke XXX</li>
          </ul>
        </div>
        <div class="tovar_item">
          <div class="tovar_btn">
            <button><img src="./assets/heart.svg"> Favoriten</button>
            <button><img src="./assets/copy.svg"> Kopieren</button>
            <button><img src="./assets/printing.svg"> Drucken</button>
          </div>
          <div class="tovar_zakaz">
            <div class="tovar_prise">
              <span>
                <s>1.349,00 €</s>
              </span>
              1.199,00 €
            </div>
            <div class="tovar_ink">
              inkl. 19% MwSt. zzgl. <a href="#">Versandkosten</a>
            </div>
            <div class="tovar_buy">
              <div class="select-container">
                <select name="number_select" id="number_select">
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                </select>
              </div>
              <button class="to_basket">In den Warenkorb</button>
              <button class="to_buy">Konfigurieren</button>
            </div>
          </div>
        </div>
      </nav>
    </section>
    <section class="tab">
      <Tab />
    </section>
  </main>
</template>
<style lang="scss">
.tovar{
  display: flex;
  justify-content: space-around;
  font-family: "Roboto", sans-serif;
  margin-top: 20px;
  flex-wrap: wrap;
}
.tovar_items{
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  .tovar_item h1{
    max-width: 690px;
    font-weight: 600;
    font-size: 20px;
    line-height: 23.44px;
    color: #333;
    padding-bottom: 10px;
    border-bottom: 1px solid #ccc;
  }
  .tovar_item li{
    font-weight: 400;
    font-size: 18px;
    line-height: 24.21px;
    color: #333;
  }
  .tovar_btn{
    display: flex;
    border: 1px solid #ccc;
    border-radius: 10px;   
    max-width: 690px;
    padding: 10px 0;
    margin-bottom: 20px;
    color: #4c4c4c;
    button{
      width: 230px;
      border-style: none;
      outline-style: none;
      background-color: #fff;
      cursor: pointer;
      &:nth-child(2){
        border-left: 1px solid #ccc;
        border-right: 1px solid #ccc;
      }
    }
  }
}
.tovar_zakaz{
  display: flex;
  flex-direction: column;
  padding: 20px;
  max-width: 690px;
  border: 1px solid #ccc;
  border-radius: 10px;
  .tovar_prise{
    display: flex;
    justify-content: flex-end;
    align-items: flex-end;
    font-weight: 600;
    font-size: 30px;
    line-height: 40.36px;
    color: #333;
    margin-bottom: 5px;
    span{
      font-weight: 400;
      line-height: 26.9px;
      font-size: 20px;
      color: #a6a6a6;
    }
  }
  .tovar_ink{
    display: flex;
    justify-content: flex-end;
    align-items: flex-end;
    font-weight: 400;
    font-size: 12px;
    line-height: 16.4px;
    color: #808080;
    margin-bottom: 10px;
    a{
      color: #808080;
    }
  }
}
.tovar_buy{
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  select{
    all: unset;
    display: flex;
    justify-content: center;
    align-items: center;
    padding-left: 5px;
    background-color: #d1d1d19e;
    width: 60px;
    height: 30px;
    position: relative;
    cursor: pointer;
    z-index: 10;
  }
  button{
    border-radius: 10px;
    width: 270px;
    border-style: none;
    outline-style: none;
    color: #fff;
    cursor: pointer;
    font-size: 18px;
    font-weight: 500;
    line-height: 24.21px;
  }
}
.select-container {
  position: relative;
  &::after {
    content: '';
    position: absolute;
    background-image: url('./assets/select.svg');
    background-repeat: no-repeat;
    width: 20px;
    height: 20px;
    top: 5px;
    right: 10px;
    z-index: 0;
  }
}
.to_basket{
  background: #1D1347;
}
.to_buy{
  background: #00C72C;
}
@media (max-width: 1180px){
  .tovar{
    align-items: center;
  }
}
@media (max-width: 700px){
  h1{
    width: 350px;
    padding: 0 5px;
  }
  .tovar_btn{
    flex-direction: column;
    justify-content: center;
    max-width: 230px!important;
  }
  .tovar_btn{
    button{
      &:nth-child(2){
        border-left: thick!important;
        border-right: thick!important;
      }
    }
  }
  .tovar_item{
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .tovar_buy{
    flex-direction: column;
    align-items: center;
    button{
      margin: 10px 0;
    }
    .select-container::after {
      right: 4px;
    }
  }
}
</style>