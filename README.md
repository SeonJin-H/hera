# Markup-Project-HERA
자바스크립트 및 제이쿼리를 이용한 반응형 쇼핑몰 웹사이트 구축(개인프로젝트)

![목업](https://github.com/SeonJin-H/hera/blob/main/hera_mockup.png)
Demo: <http://jin1404.dothome.co.kr>


### 📑 개발 목표
* CSS 스타일 선택자 활용
* 제이쿼리의 다양한 메소드 활용을 통한 라이브러리 대체 형식 이해
* 미디어 쿼리를 이용한 반응형 웹페이지 구축


### 🛠️ 사용 기술
* HTML
* CSS
* jQuery
* Media Query 


### 💎 주요 기능
* 자바스크립트 및 제이쿼리에서 제공하는 메소드를 이용한 슬라이드 무한루프 동작 및 재생정지 기능 구현
![작동예시](https://github.com/SeonJin-H/hera/blob/main/proto01.png)
~~~
var index = 1; 
var slide_click_s = true;  //클릭연사방지
var slide_play_s = true;  //재생정지버튼

function slide(e){  //버튼클릭
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

function dot(e){  //페이지네이션
  index = e;
  $('#main_slide ul').css({'left' : index * -100 + '%', 'transition' : '0.3s'});
  $('#main_slide .button .dot a').css('width', '14px');
  $('#main_slide .button .dot a').eq(index - 1).css('width', '25px');

}

var play_stop = setInterval(function() {  //재생정지
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

* 제어문을 이용한 플러그인 기능 모방 이동 슬라이드 제작 
![작동에시](https://github.com/SeonJin-H/hera/blob/main/proto02_re.png)
~~~
var num = 0; 
var num_modal = 0; 
var SWITCH = true;  //클릭연사방지

function btn(e){  //슬라이드

  if(SWITCH == true){
    SWITCH = false;
    setTimeout(function(){
      SWITCH = true;
    }, 300)

    num += e;
    if(num < 0) num = 0;
    if(num > 5) num = 5;

    $('#review>.view>ul').css('left', -250 * num + 'px');
  }

}

function view(e){  //클릭이벤트
  num_modal = e;
  $('.modal').show();
  $('.modal ul li').eq(num_modal).show();
}

function btn_modal(e){  //모달슬라이드
  num_modal += e;
  if(num_modal < 0) num_modal = 0;
  if(num_modal > 8) num_modal = 8;

  $('.modal ul li').hide();
  $('.modal ul li').eq(num_modal).show();
}

$('button.close').click(function(){
  $('.modal').hide();
  $('.modal ul li').hide();
})

//모달상세
$('#review>.modal>ul>li>.show_product').mouseover(function(){
    $('#review>.modal>ul>li>.show_product').css('opacity','1');
})
$('#review>.modal>ul>li>.show_product').mouseout(function(){
    $('#review>.modal>ul>li>.show_product').css('opacity','0');
})
~~~
* 팝업 모달 동작 설계
* 미디어 쿼리를 이용한 전체 페이지 개발


### 💡 개선 사항
* new/best 자세히보기 버튼에 hover 이벤트 추가 필요
* 모바일 모드 시 최하단 슬라이드 이동값 해결 필요

### 🖥️  작업 기여
*	웹사이트 전체 구축
*	기여도 100%
