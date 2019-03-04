<template>
  <div class="hello">
    <button @click="handlePlay">收到后端信号</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods: {
    handlePlay() {
      var audio = document.getElementById("music");
      if(audio){ // 如果已经下载过该mp3则直接播放
        audio.play();
      } else {
        var newAudio = document.createElement("audio");
        newAudio.id = "music";
        newAudio.setAttribute("preload", "preload");
        var source = document.createElement("source");
        source.src = '/static/commit_mp3.mp3';
        source.type = 'audio/mpeg';
        newAudio.appendChild(source);
        document.body.appendChild(newAudio);
        newAudio.oncanplaythrough = function (event) {
          event.target.play();
        }
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
