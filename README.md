# Markup-Project-HERA
자바스크립트 및 제이쿼리를 이용한 반응형 쇼핑몰 웹사이트 구축

Demo: <http://jin1404.dothome.co.kr>


### 🖥️ 개발 목표
제이쿼리의 다양한 메소드 사용 및 작동 방식 이해, 미디어 쿼리를 이용한 반응형 웹페이지 구축


### 🛠️ 사용 기술
* HTML
* CSS
* Javascript
* jQuery


### 💎 주요 기능
* 제이쿼리에서 제공하느 메소드를 이용한 슬라이드 무한루프 동작 및 재생정지 기능 구현
~~~
var index = 1; 
var slide_click_s = true; 
var slide_play_s = true; 

function slide(e){ 
  if(slide_click_s == true){
    slide_click_s = false;
    setTimeout(function(){
      slide_click_s = true;
    }, 300);

    index += e;
    dot(index);

    if(index >= 7){
      index = 1;
      setTimeout(function(){
        $('#main_slide ul').css({'left' : index * -100 + '%', 'transition' : '0s'});
      }, 300);
      $('#main_slide .button .dot a').eq(index - 1).css('width', '25px');  
    }

    if(index <= 0){
      index = 6;
      setTimeout(function(){
        $('#main_slide ul').css({'left' : index * -100 + '%', 'transition' : '0s'});
      }, 300);
    }
  }
}

function dot(e){ 
  index = e;
  $('#main_slide ul').css({'left' : index * -100 + '%', 'transition' : '0.3s'});
  $('#main_slide .button .dot a').css('width', '14px');
  $('#main_slide .button .dot a').eq(index - 1).css('width', '25px');

}

var play_stop = setInterval(function() { 
  slide(1);
}, 5000);

function play() {
  if(slide_play_s == true){
    slide_play_s = false;
    $('#main_slide .button .Black button img').attr('src','img/slide_play.png');
            $('#main_slide .button .White button img').attr('src','img/slide_play_W.png');
    clearInterval(play_stop);
  } else {
    slide_play_s = true;
    $('#main_slide .button .Black button img').attr('src','img/slide_stop.png');
            $('#main_slide .button .White button img').attr('src','img/slide_stop_W.png');
    play_stop = setInterval(function() {
      slide(1);
    }, 5000);
  }
}
~~~
