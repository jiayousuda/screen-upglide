<template>
  <div id="app">
    <div class="header" :style="{height:Hheight}">
      <video src="/i/movie.ogg" controls="controls">your browser does not support the video tag</video>
    </div>
    <div class="position">
      <div :style="{height:Hheight}" class="aa"></div>
      <div :style="{height:Hheight}" class="bb">我是第二屏幕</div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Home",
  data() {
    return {
      Hheight: "",
      ss: false,
      height: 0
    };
  },
  methods: {
    handleScroll() {
      let scrollTop =
        window.pageYOffset ||
        document.documentElement.scrollTop ||
        document.body.scrollTop;
      console.log(scrollTop);
      console.log(this.height / 2);
      if (scrollTop > this.height / 2) {
        this.ss = true;
      }
    }
  },

  mounted() {
    window.addEventListener("scroll", this.handleScroll);
  },
  beforeMount() {
    var h = document.documentElement.clientHeight || document.body.clientHeight;
    this.height = h;
    this.Hheight = `${h}px`;
  }
};
</script>
<style lang="less">
body {
  margin: 0;
  padding: 0;
}
.header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  background: #666;
  z-index: 0;
}
video {
  width: 100%;
  height: 100%;
}

.position {
  width: 100%;
  position: absolute;
  top: 0;
  z-index: 999;
}
.positionss {
  position: fixed;
  top: 0;
  left: 0rpx;
  right: 0rpx;
  z-index: 999;
}

.aa {
  opacity: 0.1;
  background: #f5f5f5;
}
.bb {
  background: #fff;
}
</style>

