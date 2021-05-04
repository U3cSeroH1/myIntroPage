<template>
  <div class="container">
    <div id="wrap" class="parallax_box">
      <div id="wrapChild" class="parallax_content img_bg_01">CONあTENT1</div>
      <div id="wrapChild" class="parallax_content img_bg_02">CONTENT2</div>
      <div id="wrapChild" class="parallax_content img_bg_03">CONTENT3</div>
      <div id="wrapChild" class="parallax_content img_bg_04">CONTENT4</div>
      <div id="wrapChild" class="parallax_content img_bg_05">CONTENT5</div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'





export default Vue.extend({





mounted () {
  
  // 変数
  let wrap = <HTMLInputElement>document.getElementById('wrap'),
    elements = document.querySelectorAll('#wrap #wrapChild'), // 1画面分スクロールさせる要素
    elRect : DOMRect[] = [], // 要素の位置情報を取得するための配列
    elTop : number[] = [], // 要素の位置を入れるための配列
    count = 0, // 
    wheelFlag = false;
  
  // 各要素の位置を取得
  function getElTop() {
    for (var i = 0; i < elements.length; i++) { // 要素の数ループ
      elRect.push(elements[i].getBoundingClientRect()); // 要素の位置情報を配列へ
      
    }
    for (var i = 0; i < elRect.length; i++) { // 要素の数ループ
      elTop.push(elRect[i].top + window.scrollY); // 要素の位置を配列へ
    }
  }
  getElTop();
  
  // 画面リサイズのときの処理
  window.addEventListener('resize', function () {
    elRect = []; // 位置情報の配列を一旦空に
    elTop = []; // 位置の配列を一旦空に
    getElTop(); // 位置を取得
    window.scrollTo(0, elTop[count]); // 現在表示中の画面位置へ
  });

  // マウスホイールのときの処理
  wrap.addEventListener('wheel', function (e) {
    e.preventDefault(); // デフォルトのスクロール動作を削除
    if (!wheelFlag) { // wheelFlagがfalseのときに発動
      wheelFlag = true; // wheelFlagをtrueにして無駄に発動しないように
      if (e.deltaY > 0) { // ホイールが下方向だったら
        if (count >= elements.length - 1) { // 要素の数以上に増えないようにcountが要素の数を超えたら
          count = elements.length - 1; // countを要素の数とする
        } else {
          count++; // それまではcountをプラス
        }
      } else if (e.deltaY < 0) { // ホイールが上方向だったら
        if (count <= 0) { // 0より小さくならないようにcountが0以下なら
          count = 0; // countを0とする
        } else {
          count--; // それまではcountをマイナスしていく
        }
      }
      setTimeout(function () { //0.8秒後にwheelFlagをfalseにして次のページめくれるように
        wheelFlag = false;
      },800);
      setTimeout(function () {
        window.scrollTo({ // count番目の要素へスクロール
          top: elTop[count],
          behavior: 'smooth',
        });
      },20); // スクロールまで時間差をつけて慣性スクロール対策
    }
  });
},

})

</script>

<style>



</style>
