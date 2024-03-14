<template>
  <div ref="JessibucaPlayerRef" :style="{ height: '100%', width: '100%', background: 'rgba(22,22,22, 0.8)' }"></div>
</template>

<script>
import HZPlayer from "./jPlayer.js";
export default {
  name: "hzPlayer",
  props: {
    height: {
      type: String,
      default: () => "400",
    },
    width: {
      type: String,
      default: () => "400",
    },
    videoUrl: {
      type: String,
      default: () => "",
    },
  },
  data() {
    return {
      JessibucaPlayer: null,
    };
  },
  watch: {
    videoUrl: {
      handler(val) {
        if (this.JessibucaPlayer && val) {
          this.JessibucaPlayer.play(val)
            .then(() => {
              console.log("play success");
            })
            .catch((e) => {
              console.error(e);
            });
        }
      },
      deep: true,
      immediate: true,
    },
  },
  mounted() {
    // this.JessibucaPlayer = new window.JessibucaPro({
    this.JessibucaPlayer = new HZPlayer({
      container: this.$refs.JessibucaPlayerRef,
      videoBuffer: 0.2, // 最大缓冲时长，单位秒
      isResize: false,
      loadingText: "正在加载中",
      showBandwidth: true, // 显示网速
      // decoder: './jessibucaPro-demo/decoder-pro.js',
      // decoder: './jessibucaPro/decoder-pro.js',
      decoder: "./hzPlayer/src/decoder-pro.js",
      useMSE: true,
      useWCS: true,
      useSIMD: true,
      autoWasm: true,
      rotate: 0,
      isFlv: true,
      hasAudio: false,
      controlAutoHide: true,
      supportDblclickFullscreen: false, // 是否支持屏幕的双击事件，触发全屏，取消全屏事件。
      operateBtns: {
        fullscreen: true,
        screenshot: true,
        play: false,
        audio: true,
        record: true,
        // ptz: true,
        // quality: true,
        // close: true,
        // zoom: true,
        // performance: true,
        // scale: true,
      },
      isNotMute: false,
      heartTimeout: 10,
      ptzClickType: "mouseDownAndUp",
      ptzZoomShow: true,
      ptzMoreArrowShow: true,
      ptzApertureShow: true,
      ptzFocusShow: true,
      record: "record",
      vod: true,
      forceNoOffscreen: false,
      // useCanvasRender: false,
      // useVideoRender: true,
      useWebGPU: false,
      demuxUseWorker: false,
      // 调试参数
      // debug: true,
      // debugLevel: 'debug',
    });
  },
  beforeDestroy() {
    if (this.JessibucaPlayer) {
      this.JessibucaPlayer.destroy();
    }
  },
};
</script>
