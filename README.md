# Calculate

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Расчёт стоимости доставки</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/4.3.1/css/bootstrap-grid.min.css">
<style>
body{font-family:sans-serif;}
.orientir-price{-webkit-touch-callout: none; -webkit-user-select: none; -khtml-user-select: none; -moz-user-select: none; -ms-user-select: none; user-select: none;}
.orientir-price input[type="checkbox"],
.orientir-price label,
.orientir-price input[type="radio"] {cursor: pointer;}
.calc-orientir{background-color: #ffde00;padding: 30px;}
.calc-orientir__title{font-size: 16px;text-transform: uppercase;margin-bottom: 30px;}
.calc-orientir input{width: 100%;background-color:transparent;border:none;border-bottom: 1px solid #10262f;margin-bottom: 20px;}
.calc-orientir input::-webkit-input-placeholder {color:#10262f; opacity:1;}
.calc-orientir input::-moz-placeholder {color:#10262f; opacity:1;}
.calc-orientir input:-moz-placeholder {color:#10262f; opacity:1;}
.calc-orientir input:-ms-input-placeholder {color:#10262f; opacity:1;}
.calc-orientir .calc-orientir__name{margin-bottom: 20px;}
.calc-orientir select{
  display: block;
  width: 100%;
  margin-bottom: 20px;
  -webkit-appearance: none;
  -moz-appearance: none;
  -ms-appearance: none;
  appearance: none;
  background: #f7d12b;
  outline: 0;
  border: none;
  padding: 5px 15px;
  cursor: pointer;
}
.calc-orientir .calc-orientir__radio{display: flex;justify-content: space-around;margin-bottom: 20px;}
.calc-orientir .calc-orientir__radio input{margin-bottom: 0;margin-right: 6px;}
.calc-orientir .calc-orientir__radio label{margin-bottom: 0;}
.calc-orientir .calc-orientir__radio > div{display: flex;cursor: pointer;align-items: center;}
.calc-results{border:2px solid #ffde00;padding: 30px;}
.calc-results input{margin-right: 10px;}
.calc-results .calc-results__title{margin-bottom: 20px;text-transform: uppercase;}
.calc-results .calc-results__text{font-size: 14px;margin-bottom: 20px;}
.calc-results .calc-results__line{display: flex;justify-content: space-between;margin-bottom: 20px;}
.calc-results .calc-results__line-result{font-weight: bold;color:#18313b}
.calc-results__line-summ{font-size: 18px;font-weight: bold;text-transform: uppercase;}
@media only screen and (min-width: 1200px) {
  .calc-results__line-summ{margin-top: 55px;}
  .calc-results .calc-results__text{margin-bottom: 55px;}
}
.orientir-price .btn{
  background-color: #ffde00;font-size: 14px;text-transform: uppercase;width:140px;display: inline-block;height: 40px;cursor: pointer;text-align: center;line-height: 1.2em;padding: 3px;border:none;color:#333;
}
.orientir-price .btn:hover{text-decoration: none;}
.orientir-price .btns{display: flex;justify-content: space-between;margin-bottom: 11px;}
@media only screen and (max-width: 400px) {
  .calc-orientir .calc-orientir__radio{flex-direction: column;}
  .calc-orientir .calc-orientir__radio > div{margin-bottom: 10px;}
  .orientir-price .btns{flex-wrap: wrap;justify-content: center;}
  .orientir-price .btn{margin: 5px;}
}
  </style>
</head>
<body>


  <form class="orientir-price" id="calculate">

    <!-- Hidden Required Fields -->
    <input type="hidden" name="project_name" value="Доставка грузов из Китая">
    <input type="hidden" name="admin_email" value="rlytrue@gmail.com">
    <input type="hidden" name="form_subject" value="Форма со страницы Ориентировочный расчёт стоимости">
    <!-- END Hidden Required Fields -->

    <div class="container">
      <h1 class="title tac">Ориентировочный расчет стоимости доставки</h1>
      <div class="row">

        <div class="col-xl-8">
          <div class="calc-orientir equal_h" style="height: 590px;">
            <div class="calc-orientir__title">Информация о пользователе</div>
            <input type="text" placeholder="Ф.И.О." name="Ф.И.О.">
              <div class="row">
                <div class="col-sm-12 col-md">
                  <input type="tel" placeholder="Телефон" name="Телефон">

                  <div class="calc-orientir__name"><b>Отправитель:</b></div>

                  <select id="calc_city_send" required="">
                    <option value="0" selected="" disabled="">Город отправки</option>
                    <option value="1" name="calc_city_send1">Гуанчжоу</option>
                    <option value="2" name="calc_city_send2">Иу</option>
                    <option value="3" name="calc_city_send3">Пекин</option>
                  </select>

                  <div class="calc-orientir__name"><b>Получатель:</b></div>

                  <select id="calc_country_get" required="" onchange="calc()">
                    <option value="0" selected="" disabled="">Страна</option>
                    <option value="1">Россия</option>
                    <option value="2">Украина</option>
                    <option value="3">Казахстан</option>
                    <option value="4">Кыргызстан</option>
                  </select>

                  <select onchange="calc()" id="calc_city_get" required="">
                    <option value="0" selected="" disabled="">Город</option>
                    <option value="1" id="calc_city_get_1">Москва</option>
                    <option value="2" id="calc_city_get_2">Киев</option>
                    <option value="3" id="calc_city_get_3">Алматы</option>
                    <option value="4" id="calc_city_get_4">Бишкек</option>
                  </select>

                </div>
                <div class="col-sm-12 col-md">
                  <input type="text" placeholder="E-mail" name="E-mail" required="">

                  <div class="calc-orientir__name"><b>Параметры доставки</b></div>

                  <div class="calc-orientir__name">Типы доставок</div>

                  <div class="calc-orientir__radio types_dostavki">
                    <div>
                      <input type="radio" name="Тип доставки" id="calc_type_get1" onchange="calc()" value="Авто" required="">
                      <label for="calc_type_get1" class="calc-orientir__radio-name">Авто</label>
                    </div>
                    <div>
                      <input type="radio" name="Тип доставки" id="calc_type_get2" onchange="calc()" value="Ж/д" required="">
                      <label for="calc_type_get2" class="calc-orientir__radio-name">Ж/д</label>
                    </div>
                    <div>
                      <input type="radio" name="Тип доставки" id="calc_type_get3" onchange="calc()" value="Авиа" checked="">
                      <label for="calc_type_get3" class="calc-orientir__radio-name">Авиа</label>
                    </div>
                  </div>

                  <label for="">Цена закупленного товара ($ USA)
                    <input type="number" placeholder="" name="Цена закупленного товара ($ USA)" id="czt" required="" onchange="calc()" value="0" min="0">
                  </label>
                  <label for="">Общий вес груза (брутто, кг)
                    <input type="number" placeholder="" name="Общий вес груза (брутто, кг)" id="ovg" required="" onchange="calc()" value="0" min="0">
                  </label>
                  <label for="">Количество упаковочных мест
                    <input type="number" placeholder="" name="Количество упаковочных мест" id="kum" required="" onchange="calc()" value="0" min="0">
                  </label>

                  <div class="calc-orientir__radio">
                    <div><b>Тип груза:</b></div>
                    <div>
                      <input type="radio" name="Тип груза" id="hr" required="" onchange="calc()" checked="" value="Хрупкий">
                      <label for="hr" class="calc-orientir__radio-name">Хрупкий</label>
                    </div>
                    <div>
                      <input type="radio" name="Тип груза" id="nh" onchange="calc()" value="Не хрупкий">
                      <label for="nh" class="calc-orientir__radio-name">Не хрупкий</label>
                    </div>
                    <!-- <div>
                      <input type="radio" name="Тип груза" id="bu" onchange="calc()" value="Без упаковки">
                      <label for="bu" class="calc-orientir__radio-name">Без упаковки</label>
                    </div> -->
                  </div>

                </div>
              </div>
          </div>
        </div>

        <div class="col-xl-4">
          <div class="calc-results equal_h" style="height: 590px;">
            <div class="calc-results__title">Результаты расчета</div>
            <label>
              <input type="checkbox" name="Без учёта устраховки" value="Без учёта устраховки" id="bez_strahovki" onchange="calc()">Без учета страховки
            </label>
            
            <div class="calc-results__text">
              Расчеты калькулятора произведены по
              ориентировочным срокам и стоимости
              доставки на удельный вес груза 140-160
              кг/м<sup>3</sup>
            </div>

            <div class="calc-results__line">
              <div class="calc-results__line-text">Срок доставки:</div>
              <div class="calc-results__line-result"><span id="srok_dostavki">0</span> дней</div>
            </div>

            <div class="calc-results__line">
              <div class="calc-results__line-text">Стоимость упаковки </div>
              <div class="calc-results__line-result"><span id="stoimost_upakovki">0</span> $</div>
            </div>

            <div class="calc-results__line">
              <div class="calc-results__line-text">Стоимость доставки </div>
              <div class="calc-results__line-result"><span id="result">0</span> $</div>
            </div>

            <div class="calc-results__line">
              <div class="calc-results__line-text">Стоимость страховки </div>
              <div class="calc-results__line-result"><span id="stoimost_strahovki">0</span> $</div>
            </div>

            <div class="calc-results__line calc-results__line-summ">
              <div class="calc-results__line-text">Итого:</div>
              <div class="calc-results__line-result"><span id="result_all">0</span> $</div>
            </div>

            <div class="btns">
              <input type="hidden" name="Итого - результаты расчёта" value="0" id="result_calculate">
              <button class="btn">Отправить</button>
              <a data-fancybox="" data-src="#hidden-content" href="javascript:;" class="btn">БЕСПЛАТНАЯ <br>КОНСУЛЬТАЦИЯ</a>
            </div>

          </div>
        </div>
        
      </div>
    </div>
  </form>

  <script src="http://code.jquery.com/jquery-3.4.0.min.js" integrity="sha256-BJeo0qm959uMBGb65z40ejJYGSgR7REI4+CW1fNKwOg=" crossorigin="anonymous"></script>
<script>
  jQuery(function($){

    // Показывать select'ы в зависимости от выбора другого select'a
    $('#calc_country_get').change(function(){
      var val = $(this).val();

      if ( val == 1 ) {
        $('#calc_city_get').prop('disabled', true);
        $('#calc_city_get option').html('Москва');
        $('#calc_city_get option[value=1]').removeAttr('disabled');
        return false;

      } else if ( val == 2 ) {
        $('#calc_city_get').prop('disabled', true);
        $('#calc_city_get option').html('Киев');
        $('#calc_city_get option[value=2]').removeAttr('disabled');
        return false;

      } else if ( val == 3 ) {
        $('#calc_city_get').prop('disabled', true);
        $('#calc_city_get option').html('Алматы');
        $('#calc_city_get option[value=3]').removeAttr('disabled');
        return false;

      } else if ( val == 4 ) {
        $('#calc_city_get').prop('disabled', true);
        $('#calc_city_get option').html('Бишкек');
        $('#calc_city_get option[value=4]').removeAttr('disabled');
        return false;
      }

    });
    // / Показывать select'ы в зависимости от выбора другого select'a

    $('#calc_city_get').change(function(){
      var val = $(this).val();
      if ( val == 1 ) {
        $('.calc-orientir .types_dostavki > div').fadeIn(0);
      } else if ( val == 2 ) {
        $('.calc-orientir .types_dostavki > div').fadeIn(0);
        $('.calc-orientir .types_dostavki > div:nth-child(1)').fadeOut(0);
      } else if ( val == 3 ) {
        $('.calc-orientir .types_dostavki > div').fadeIn(0);
      }
      else if ( val == 4 ) {
        $('.calc-orientir .types_dostavki > div').fadeIn(0);
        $('.calc-orientir .types_dostavki > div:nth-child(1), .calc-orientir .types_dostavki > div:nth-child(2)').fadeOut(0);
      }
    });

    $('#calc_country_get').change(function(){
      var val = $(this).val();
      if ( val == 1 ) {
        $('.calc-orientir .types_dostavki > div').fadeIn(0);
      } else if ( val == 2 ) {
        $('.calc-orientir .types_dostavki > div').fadeIn(0);
        $('.calc-orientir .types_dostavki > div:nth-child(1)').fadeOut(0);
      } else if ( val == 3 ) {
        $('.calc-orientir .types_dostavki > div').fadeIn(0);
      }
      else if ( val == 4 ) {
        $('.calc-orientir .types_dostavki > div').fadeIn(0);
        $('.calc-orientir .types_dostavki > div:nth-child(1), .calc-orientir .types_dostavki > div:nth-child(2)').fadeOut(0);
      }
    });

  });

  /*
    * Расчёт стоимости доставки
    */
  function calc() {
      
    var czt = document.getElementById("czt");       // цена товара
    var ovg = document.getElementById("ovg");       // общий вес груза
    var kum = document.getElementById("kum");       // количество мест

    var srok_dostavki = document.getElementById("srok_dostavki"); // ссылка срок доставки
    var result = document.getElementById("result"); // ссылка СТОИМОСТЬ ДОСТАВКИ

    var stoimost_strahovki = document.getElementById("stoimost_strahovki"); // ссылка СТОИМОСТЬ страховки

    var stoimost_upakovki = document.getElementById("stoimost_upakovki"); // ссылка СТОИМОСТЬ упаковки

    var bez_strahovki = document.getElementById("bez_strahovki"); // без учёта страховки

    var result_calculate = document.getElementById("result_calculate");

    var price = 0;                // СТОИМОСТЬ ДОСТАВКИ


    // ____________________________________
    // расчёт стоимости доставки

    // Для Москвы
    if ( jQuery('#calc_country_get').val() == 1 ) {

      // Выбран Авто
      if ( jQuery('#calc_type_get1').prop('checked') ) {
        // если выбран НЕхрупкий груз 
        if ( jQuery('#hr').prop('checked') ) {
          price = parseInt(ovg.value) * 3.5 + parseInt(kum.value) * 15 + parseInt(czt.value) * 0.02 ;
        } // / если выбран хрупкий груз

        // если выбран НЕхрупкий груз
        if ( jQuery('#nh').prop('checked') ) {
          price = parseInt(ovg.value) * 3.5 + parseInt(kum.value) * 10 + parseInt(czt.value) * 0.02 ;
        }// / если выбран НЕхрупкий груз
      }

      // Выбран Ж/Д
      if ( jQuery('#calc_type_get2').prop('checked') ) {
        // если выбран НЕхрупкий груз 
        if ( jQuery('#hr').prop('checked') ) {
          price = parseInt(ovg.value) * 4 + parseInt(kum.value) * 15 + parseInt(czt.value) * 0.02 ;
        } // / если выбран хрупкий груз

        // если выбран НЕхрупкий груз
        if ( jQuery('#nh').prop('checked') ) {
          price = parseInt(ovg.value) * 4 + parseInt(kum.value) * 10 + parseInt(czt.value) * 0.02 ;
        }// / если выбран НЕхрупкий груз
      }

      // Выбран Авиа
      if ( jQuery('#calc_type_get3').prop('checked') ) {
        // если выбран НЕхрупкий груз 
        if ( jQuery('#hr').prop('checked') ) {
          price = parseInt(ovg.value) * 4.5 + parseInt(kum.value) * 15 + parseInt(czt.value) * 0.02 ;
        } // / если выбран хрупкий груз

        // если выбран НЕхрупкий груз
        if ( jQuery('#nh').prop('checked') ) {
          price = parseInt(ovg.value) * 4.5 + parseInt(kum.value) * 10 + parseInt(czt.value) * 0.02 ;
        }// / если выбран НЕхрупкий груз
      }

    }// / Для Москвы


    // Для Киева
    if ( jQuery('#calc_country_get').val() == 2 ) {

      // Выбран Ж/Д
      if ( jQuery('#calc_type_get2').prop('checked') ) {
        // если выбран НЕхрупкий груз 
        if ( jQuery('#hr').prop('checked') ) {
          price = parseInt(ovg.value) * 7.5 + parseInt(kum.value) * 15 + parseInt(czt.value) * 0.02 ;
        } // / если выбран хрупкий груз

        // если выбран НЕхрупкий груз
        if ( jQuery('#nh').prop('checked') ) {
          price = parseInt(ovg.value) * 7.5 + parseInt(kum.value) * 10 + parseInt(czt.value) * 0.02 ;
        }// / если выбран НЕхрупкий груз
      }

      // Выбран Авиа
      if ( jQuery('#calc_type_get3').prop('checked') ) {
        // если выбран НЕхрупкий груз 
        if ( jQuery('#hr').prop('checked') ) {
          price = parseInt(ovg.value) * 8.5 + parseInt(kum.value) * 15 + parseInt(czt.value) * 0.02 ;
        } // / если выбран хрупкий груз

        // если выбран НЕхрупкий груз
        if ( jQuery('#nh').prop('checked') ) {
          price = parseInt(ovg.value) * 8.5 + parseInt(kum.value) * 10 + parseInt(czt.value) * 0.02 ;
        }// / если выбран НЕхрупкий груз
      }

    }// / Для Киева


    // Для Алматы
    if ( jQuery('#calc_country_get').val() == 3 ) {

      // Выбран Авто
      if ( jQuery('#calc_type_get1').prop('checked') ) {
        // если выбран НЕхрупкий груз 
        if ( jQuery('#hr').prop('checked') ) {
          price = parseInt(ovg.value) * 2.5 + parseInt(kum.value) * 15 + parseInt(czt.value) * 0.02 ;
        } // / если выбран хрупкий груз

        // если выбран НЕхрупкий груз
        if ( jQuery('#nh').prop('checked') ) {
          price = parseInt(ovg.value) * 2.5 + parseInt(kum.value) * 10 + parseInt(czt.value) * 0.02 ;
        }// / если выбран НЕхрупкий груз
      }

      // Выбран Ж/Д
      if ( jQuery('#calc_type_get2').prop('checked') ) {
        // если выбран НЕхрупкий груз 
        if ( jQuery('#hr').prop('checked') ) {
          price = parseInt(ovg.value) * 3.5 + parseInt(kum.value) * 15 + parseInt(czt.value) * 0.02 ;
        } // / если выбран хрупкий груз

        // если выбран НЕхрупкий груз
        if ( jQuery('#nh').prop('checked') ) {
          price = parseInt(ovg.value) * 3.5 + parseInt(kum.value) * 10 + parseInt(czt.value) * 0.02 ;
        }// / если выбран НЕхрупкий груз
      }

      // Выбран Авиа
      if ( jQuery('#calc_type_get3').prop('checked') ) {
        // если выбран НЕхрупкий груз 
        if ( jQuery('#hr').prop('checked') ) {
          price = parseInt(ovg.value) * 4 + parseInt(kum.value) * 15 + parseInt(czt.value) * 0.02 ;
        } // / если выбран хрупкий груз

        // если выбран НЕхрупкий груз
        if ( jQuery('#nh').prop('checked') ) {
          price = parseInt(ovg.value) * 4 + parseInt(kum.value) * 10 + parseInt(czt.value) * 0.02 ;
        }// / если выбран НЕхрупкий груз
      }

    }// / Для Алматы


    // Для Киева
    if ( jQuery('#calc_country_get').val() == 4 ) {

      // Выбран Авиа
      if ( jQuery('#calc_type_get3').prop('checked') ) {
        // если выбран НЕхрупкий груз 
        if ( jQuery('#hr').prop('checked') ) {
          price = parseInt(ovg.value) * 3.5 + parseInt(kum.value) * 15 + parseInt(czt.value) * 0.02 ;
        } // / если выбран хрупкий груз

        // если выбран НЕхрупкий груз
        if ( jQuery('#nh').prop('checked') ) {
          price = parseInt(ovg.value) * 3.5 + parseInt(kum.value) * 10 + parseInt(czt.value) * 0.02 ;
        }// / если выбран НЕхрупкий груз
      }

    }// / Для Киева
    // / расчёт стоимости доставки
    // ____________________________________

    result.innerHTML = price; // стоимость доставки


    // Сроки доставки
    if ( jQuery('#calc_type_get1').prop('checked') ) {
      price_srok_dostavki = "18-25";
    } else if ( jQuery('#calc_type_get2').prop('checked') ) {
      price_srok_dostavki = "18-20";
    } else if ( jQuery('#calc_type_get3').prop('checked') ) {
      price_srok_dostavki = "8-12";
    }
    srok_dostavki.innerHTML = price_srok_dostavki; // срок доставки


    // Стоимость упаковки
    if ( jQuery('#hr').prop('checked') ) {
      price_stoimost_upakovki = parseInt(kum.value) * 15;
    } // / если выбран хрупкий груз
    // если выбран НЕхрупкий груз
    if ( jQuery('#nh').prop('checked') ) {
      price_stoimost_upakovki = parseInt(kum.value) * 10;
    }// / если выбран НЕхрупкий груз
    // / Стоимость упаковки
    stoimost_upakovki.innerHTML = price_stoimost_upakovki; // стоимость упаковки



    // ЧЕКБОКС - СО СТРАХОВКОЙ ИЛИ БЕЗ НЕЁ - ИТОГ
    // Без учёта страховки
    if ( jQuery('#bez_strahovki').prop('checked') ) {

      // Стоимость страховки
      price_stoimost_strahovki = 0;
      stoimost_strahovki.innerHTML = price_stoimost_strahovki; // стоимость страховки

      result_all.innerHTML = parseInt(price);// итого
      result_calculate.value = parseInt(price);// итого на e-mail

    } else { // С учётом страховки

      // Стоимость страховки
      price_stoimost_strahovki = parseInt(czt.value) * 0.02;
      stoimost_strahovki.innerHTML = price_stoimost_strahovki; // стоимость страховки

      result_all.innerHTML = parseInt(price) + price_stoimost_strahovki; // итого
      result_calculate.value = parseInt(price) + price_stoimost_strahovki; // итого на e-mail
    }


  }
</script>
</body>
</html>
```
