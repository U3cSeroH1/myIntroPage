<template>
  <div class="container">
    <div class="fixedBox">
      <button
        id="upBtn"
        class="hbtn hb-fill-top-bg fixed"
        type="button"
        v-on:click="buttonClicked(true)"
      >
        UP
      </button>
      <button
        id="downBtn"
        class="hbtn hb-fill-bottom-bg fixed"
        type="button"
        v-on:click="buttonClicked(false)"
      >
        DOWN
      </button>
    </div>
    <ContentWrap />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import ContentWrap from "~/components/ContentWrap.vue";

export default Vue.extend({
  components: { ContentWrap },

  data() {
    return {
      elements: document.querySelectorAll("#wrap #wrapChild"), // 1画面分スクロールさせる要素
      elRect: [] as DOMRect[], // 要素の位置情報を取得するための配列
      elTop: [] as number[], // 要素の位置を入れるための配列
      count: 0, // 現在の位置
      wheelFlag: false,
      upBtn: <HTMLInputElement>document.getElementById("upBtn"),
      downBtn: <HTMLInputElement>document.getElementById("downBtn"),
    };
  },

  methods: {
    getElTop() {
      for (var i = 0; i < this.elements.length; i++) {
        this.elRect.push(this.elements[i].getBoundingClientRect()); // 要素の位置情報を配列へ
      }
      for (var i = 0; i < this.elRect.length; i++) {
        this.elTop.push(this.elRect[i].top + window.scrollY); // 要素の位置を配列へ
      }
    },
    resizeFunction() {
      this.elRect = []; // 位置情報の配列を一旦空に
      this.elTop = []; // 位置の配列を一旦空に
      this.getElTop(); // 位置を取得
      window.scrollTo(0, this.elTop[this.count]); // 現在表示中の画面位置へ
    },
    wheelFunction(e: WheelEvent) {
      e.preventDefault(); // デフォルトのスクロール動作を削除
      if (this.wheelFlag) return;

      this.wheelFlag = true; // wheelFlagをtrueにして無駄に発動しないように
      if (e.deltaY > 0 && this.count < this.elements.length - 1) {
        this.count++; // それまではcountをプラス
      }
      if (e.deltaY < 0 && this.count > 0) {
        this.count--; // それまではcountをマイナスしていく
      }

      setTimeout(this.wheelFlagFalse, 800);
      setTimeout(this.wheelInertiaMeasures, 20); // スクロールまで時間差をつけて慣性スクロール対策
    },
    buttonClicked(UPorDOWN: Boolean) {
      if (this.wheelFlag) return;

      this.wheelFlag = true; // wheelFlagをtrueにして無駄に発動しないように

      if (this.count > 0 && UPorDOWN) {
        this.count--; // それまではcountをマイナスしていく
      }
      if (this.count < this.elements.length - 1 && !UPorDOWN) {
        this.count++; // それまではcountをプラス
      }
      setTimeout(this.wheelFlagFalse, 100);
      setTimeout(this.wheelInertiaMeasures, 20); // スクロールまで時間差をつけて慣性スクロール対策
    },
    wheelFlagFalse() {
      this.wheelFlag = false;
    },
    wheelInertiaMeasures() {
      window.scrollTo({
        top: this.elTop[this.count],
        behavior: "smooth",
      });
    },
  },

  mounted() {
    // 各要素の位置を取得(スクロールのためのDOM取得方法)
    this.elements = document.querySelectorAll("#wrap #wrapChild"); // 1画面分スクロールさせる要素
    // 各要素の位置を取得
    this.getElTop();
    // 画面リサイズのときの処理
    window.addEventListener("resize", this.resizeFunction);
    // マウスホイールのときの処理
    window.addEventListener("wheel", this.wheelFunction, { passive: false });
  },
});
</script>
