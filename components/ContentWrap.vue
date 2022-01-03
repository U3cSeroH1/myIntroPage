<template>
  <div id="wrap" class="parallax_box">
    <div id="wrapChild" class="parallax_content img_bg_01">
      <!-- このWrapChild内に要素を入れる -->
      <TopPage />
    </div>
    <div id="wrapChild" class="parallax_content img_bg_02">
      <MultiplayerFPS />
    </div>
    <div id="wrapChild" class="parallax_content img_bg_03">
      <VRPlayGround />
    </div>
    <div id="wrapChild" class="parallax_content img_bg_04">
      <VRChatWorld />
    </div>
    <div id="wrapChild" class="parallax_content img_bg_05">
      <InProgres />
    </div>
    <div id="wrapChild" class="parallax_content img_bg_06">
      <Copylight />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import InProgres from "~/components/InProgres.vue";
import MultiplayerFPS from "~/components/MultiplayerFPS.vue";
import TopPage from "~/components/TopPage.vue";
import VRChatWorld from "~/components/VRChatWorld.vue";
import VRPlayGround from "~/components/VRPlayGround.vue";
import Copylight from "./copylight.vue";
export default Vue.extend({
  components: {
    MultiplayerFPS,
    VRPlayGround,
    VRChatWorld,
    InProgres,
    TopPage,
    Copylight,
  },
});
</script>