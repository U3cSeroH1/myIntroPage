<template>
  <div class="container">

    <div class=fixedBox>
        <button id="upBtn" class="hbtn hb-fill-top-bg fixed" type="button"> 
            <div class="">UP</div>  
        </button>
        <button id="downBtn" class="hbtn hb-fill-bottom-bg fixed" type="button">
            <div class="">DOWN</div>  
        </button>
    </div>

    <div id="wrap" class="parallax_box">

      <div id="wrapChild" class="parallax_content img_bg_01">

        <!-- このWrapChild内に要素を入れる -->


        <div class="box fade-in "> <a href="https://github.com/U3cSeroH1" class="myNameIcon poyopoyo"></a> </div>
        

        <div class="context myName fade-in">DeraPomBe's Portforio</div>



        <div class="gridcontainer">

            <div class="grid">
                <img class="gridimg" src="~/static/create/01ESZ37QD6WQ00JQBME08GW3A3.png">
            </div>
            <div class="grid">
                <div class="text">
                    <h2>wanna be Engineer</h2>
                    <p>a Engineer who is long long sleeping</p>
                </div>
            </div>
            <div class="grid">
                <img class="gridimg" src="~/static/create/01F8KQAT4A62VX7NGXE7HAM1D5.jpeg">
            </div>
            <div class="grid">
                <div class="pic">
                    <h2>VRChat</h2>
                    <img class="gridimg" src="~/static/create/12d65f32ac17e7b163df71bac9da596f.jpg">
                    <p>creating world</p>
                </div>
                
            </div>
                        <div class="grid">
                <img class="gridimg" src="~/static/create/9f52c275e48e26617d81995c5ddff47c.png">
            </div>
                        <div class="grid">
                <img class="gridimg" src="~/static/create/ccae212702f96708d94dc89aa6ef9638.png">
            </div>
                                    <div class="grid">
                <img class="gridimg" src="~/static/create/a6451e7aac0469ec1e7ca15ab24bfbc6.jpg">
            </div>
            <div class="grid">
                <div class="text">
                    <h2>VR/Action</h2>
                </div>
            </div>
                                    <div class="grid">
                <img class="gridimg" src="~/static/create/aef9df6652ee2b16c3f123d36fe3d284.png">
            </div>
                                    <div class="grid">
                <img class="gridimg" src="~/static/create/c07a79759cb901350fd9428e386f26b1.jpg">
            </div>
                                    <div class="grid">
                <img class="gridimg" src="~/static/create/ce0c91ba9ba27af8f4181473bb16bcd0.png">
            </div>

            <div class="grid">
                <div class="pic">
                    <h2>Unity</h2>
                    <img class="gridimg" src="~/static/create/e20706bde0bcba86eb6c42af262af93a.png">
                    <p>inventory</p>
                </div>
            </div>
            <div class="grid">
                <div class="text">
                    <h2>Game & Web</h2>
                    <p>sugoi kakkoii eigo mitaini mieru bunsyou. eigo wakannaine. dakaratekitounikaiteiruyo. yappari eigo kakaretetara kakkoiizyan? souomotte kaitandayo korewo yondeiru anataha surudoi. mettya sugoi. yotabanasi dakedo kono po-toforio saitoha daitai nisyuukande tukuttayo nidoto typescript tukaitaku nainaa tte omotta. tehepero.</p>
                </div>
            </div>
            <div class="grid">
                <div class="pic">
                    <h2>Animation</h2>
                    <img class="gridimg" src="~/static/create/f533eb347997fe40d11741d06f9fd76c.png">
                    <p>adding keyflame</p>
                </div>
            </div>
            <div class="grid">
                <img class="gridimg" src="~/static/create/fb8404eae7b0b2ef616ed8637a13588b.png">
            </div>
        </div>

      </div>
      <div id="wrapChild" class="parallax_content img_bg_02">

        <!-- このWrapChild内に要素を入れる -->
        <div class="commentSpace" >

            <div class="normalcontext">VRChat World
                <div class="normalcontextsmall">
                    auto
                </div>
            
            </div>

        </div>
        

    </div>
      <div id="wrapChild" class="parallax_content img_bg_03">

        <!-- このWrapChild内に要素を入れる -->
        <div class="commentSpace" >

            <div class="normalcontext">VRChat World
                <div class="normalcontextsmall">
                    auto
                </div>
            
            </div>

        </div>

      </div>
      <div id="wrapChild" class="parallax_content img_bg_04">

        <!-- このWrapChild内に要素を入れる -->
                <div class="commentSpace" >
                    <div class="normalcontext">VRChat World
                        <div class="normalcontextsmall">
                            auto
                        </div>
                    
                    </div>
                </div>



      </div>
      <div id="wrapChild" class="parallax_content img_bg_05">

        <!-- このWrapChild内に要素を入れる -->
                <div class="commentSpaceUP" >

<div class="normalcontext">Work In Progress</div>

                </div>

      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'



export default Vue.extend({


  methods: {
      Down() {
        
      },
      Up() {
        
      }
    },


mounted () {
  
  // 変数
  let wrap = <HTMLInputElement>document.getElementById('wrap'),
    elements = document.querySelectorAll('#wrap #wrapChild'), // 1画面分スクロールさせる要素
    elRect : DOMRect[] = [], // 要素の位置情報を取得するための配列
    elTop : number[] = [], // 要素の位置を入れるための配列
    count : number = 0, // 現在の位置
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


  let upBtn = <HTMLInputElement>document.getElementById('upBtn');
  let downBtn = <HTMLInputElement>document.getElementById('downBtn');

  upBtn.addEventListener('click', function(e) {
    
    e.preventDefault(); // デフォルトのスクロール動作を削除
        if (!wheelFlag) { // wheelFlagがfalseのときに発動
        wheelFlag = true; // wheelFlagをtrueにして無駄に発動しないように

            if (count <= 0) { // 0より小さくならないようにcountが0以下なら
            count = 0; // countを0とする
            } else {
            count--; // それまではcountをマイナスしていく
            }
        
        setTimeout(function () { //0.8秒後にwheelFlagをfalseにして次のページめくれるように
            wheelFlag = false;
        },100);
        setTimeout(function () {
            window.scrollTo({ // count番目の要素へスクロール
            top: elTop[count],
            behavior: 'smooth',
            });
        },20); // スクロールまで時間差をつけて慣性スクロール対策
        }
    
  }, false);
  downBtn.addEventListener('click', function(e) {
    
e.preventDefault(); // デフォルトのスクロール動作を削除
    if (!wheelFlag) { // wheelFlagがfalseのときに発動
      wheelFlag = true; // wheelFlagをtrueにして無駄に発動しないように

        if (count >= elements.length - 1) { // 要素の数以上に増えないようにcountが要素の数を超えたら
          count = elements.length - 1; // countを要素の数とする
        } else {
          count++; // それまではcountをプラス
        }

      setTimeout(function () { //0.8秒後にwheelFlagをfalseにして次のページめくれるように
        wheelFlag = false;
      },100);
      setTimeout(function () {
        window.scrollTo({ // count番目の要素へスクロール
          top: elTop[count],
          behavior: 'smooth',
        });
      },20); // スクロールまで時間差をつけて慣性スクロール対策
    }
    
  }, false);



  },

})



</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Indie+Flower&display=swap');


.fixedBox{
  position: fixed; /* 要素の位置を固定する */
  /* left:50%; */
  top:93%;
  justify-content: center;
  align-items: center;
  text-align: center;
  width: 100%; /* 幅を指定する */
   
  z-index: 10;
}


.fixed {
  width:40%;
  
  justify-content: center;
  align-items: center;
  text-align: center;
  background: rgba(0, 0, 0, 0.775);
    font-family:'Indie Flower', cursive;
  
}


#wrapChild {
  position:relative ;
  display: block;
  z-index: 0;
  /* flex-flow: column; */
}


.myName {
  position: fixed;
  display: flex;

  top: 25%;

  background-color: rgba(0, 0, 0, 0.775);

  height: 10rem;
  width: 100%;

  justify-content: center;
  align-items: center;
  text-align: center;

  z-index: 10;

    transform:rotate(-30deg);

}

.myNameIcon {
  position: fixed;
  display: flex;

    background-image: url("~/static/github_logo_icon_143772.png");

    top: 40%;
  height: 6rem;
  width: 6rem;

    margin:0 auto;

  justify-content: center;
  align-items: center;
  text-align: center;

  background-position: center;
    background-size:6rem auto;
  background-repeat: no-repeat;
  z-index: 8;


}

.box {
      position: fixed;
  display: flex;
  width:100%;
  
  justify-content: center;
  align-items: center;
  text-align: center;
  background: rgba(0, 0, 0, 0.775);
    font-family:'Indie Flower', cursive;

      z-index: 1230;
  
}

.commentSpace {
  position:absolute ;
  display: flex;

  background-color: rgba(0, 0, 0, 0.775);

    top: 70%;

  height: 30%;
  width: 100%;

  /* justify-content: center;
  align-items: center;
  text-align: center; */


  z-index: 3;
}

.commentSpaceUP {
  position:absolute ;
  display: flex;

  background-color: rgba(0, 0, 0, 0.775);

    top:20%;

  height: 20%;
  width: 100%;

  /* justify-content: center;
  align-items: center;
  text-align: center; */


  z-index: 3;
}

.context {
  position: fixed;
  /* font */
  font-size: 7vw;
  color: antiquewhite;
  font-family:'Indie Flower', cursive;


  width: 100%;
  justify-content: center;
  align-items: center;
  text-align: center;

  z-index: 20;
}

  @media (max-width: 700px) {
    .context {
      font-size: 3rem;
    }
  }
  @media (min-width: 1200px) {
    .context {
      font-size: 6rem;
    }
  }

.normalcontext {
  position: absolute;
  /* font */
    font-size: 4rem;
  color: antiquewhite;
  font-family:'Indie Flower', cursive;

height: 50%;

  width: 100%;
  justify-content: center;
  align-items: center;
  text-align: center;

  z-index: 20;
}

  @media (max-width: 700px) {
    .context {
      font-size: 3rem;
    }
  }
  @media (min-width: 1200px) {
    .context {
      font-size: 6rem;
    }
  }

  @media (max-width: 700px) {
    .normalcontext {
      font-size: 4rem;
    }
  }
  @media (min-width: 1200px) {
    .normalcontext {
      font-size: 4rem;
    }
  }

.normalcontextsmall {
  position: absolute;
  /* font */
font-size: 3rem;
  color: antiquewhite;
  font-family:'Indie Flower', cursive;

height: 40%;
margin-top: -1rem;
  width: 100%;
  justify-content: center;
  align-items: center;
  text-align: center;

  z-index: 20;
}

.btnMenu {
  position:absolute ;
  display: flex;
  bottom: 50%;

  height: 20vh;
  width: 100%;
  /* padding-top: 50vh; */
  /* padding-left: 50vh; */
  /* padding-bottom: 50vh; */
  /* padding-right: 50vh; */
  justify-content: center;
  align-items: center;
  text-align: center;
  /* background-attachment: fixed; */
  /* background-position: center; */
  /* background-size: cover; */
  /* background-repeat: no-repeat; */

  z-index: 2;
}

</style>
