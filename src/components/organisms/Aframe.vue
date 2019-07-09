<template>
  <div>
    <a-scene
      embedded
      xrweb="disableWorldTracking: true"
      xrextras-gesture-detector
      xrextras-almost-there
      xrextras-loading
      xrextras-runtime-error
    >
      <a-assets>
        <!-- Credit to Poly by Google for the model: https://poly.google.com/view/dA5osnS0Rzj -->

        <img
          id="jelly-thumb"
          src="/video-target.jpg"
        >
        <video
          id="jelly-video"
          autoplay
          muted
          loop="true"
          src="/jellyfish-video.mp4"
        />
      </a-assets>

      <a-camera
        position="0 4 10"
        raycaster="objects: .cantap"
        cursor="fuse: false; rayOrigin: mouse;"
      />

      <a-light
        type="directional"
        intensity="0.5"
        position="1 1 1"
      />

      <a-light
        type="ambient"
        intensity="1"
      />

      <!-- Note: "name:" must be set to the name of the image target uploaded to the 8th Wall Console -->
      <a-entity
        xrextras-named-image-target="name: video-target"
        xrextras-play-video="video: #jelly-video; thumb: #jelly-thumb; canstop: true"
        geometry="primitive: plane; height: 1; width: 0.79;"
      />

      <!-- <a-node /> -->
    </a-scene>
  </div>
</template>

<script>
export default {
  data () {
    console.log('aha');
    return {
      test: false
    };
  },

  mounted () {
    global.document.querySelector('a-assets').addEventListener('loaded', () => {
      console.log('ASSETS LOADED');
      this.test = true;
    });
    document.querySelector('a-scene').addEventListener('xrimagescanning', (e) => {
      console.log('IMAGE SCANNING', e);
    });
    document.querySelector('a-scene').addEventListener('xrimagefound', (e) => {
      console.log('IMAGE FOUND', e);
    });
    document.querySelector('a-scene').addEventListener('xrimageupdated', (e) => {
      console.log('IMAGE UPDATED', e);
    });
    document.querySelector('a-scene').addEventListener('xrimagelost', (e) => {
      console.log('IMAGE LOST', e);
    });

    // var js_script = document.createElement('script');
    // js_script.type = 'text/javascript';
    // js_script.src = '//apps.8thwall.com/xrweb?appKey=z1PVjAcyeuxj4mgjn4lp9aDlAiiiEUBtBvMZaw8Lw8RI98sLKdkzab2UI1YWXWOV2cmSOO';
    // js_script.async = true;
    // document.getElementsByTagName('head')[0].appendChild(js_script);
  }
};
</script>

<style>
</style>
