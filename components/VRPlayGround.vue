<template>
  <div>
    <!-- このWrapChild内に要素を入れる -->
    <div class="commentSpace">
      <div class="normalcontext">
        VR PlayGround
        <div class="normalcontextsmall">enhancing VR experience</div>
      </div>
    </div>
    <div class="videoSpaceBox">
      <iframe
        class="videoSpace"
        src="https://www.youtube.com/embed/hKE-ComPz_E"
        title="YouTube video player"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
      ></iframe>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({});
</script>