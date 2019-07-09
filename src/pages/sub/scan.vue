<i18n>
{
  "en": {

  },
  "de": {

  }
}
</i18n>

<template>
  <div class="test">
    <no-ssr>
      <aframe />
    </no-ssr>
  </div>
</template>

<script>

export default {
  components: {
    Aframe: () => process.client && import('@/components/organisms/Aframe')
  },
  data () {
    return {

    };
  },

  head () {
    return {
      title: 'title of page',
      script: [
        { src: '//cdn.8thwall.com/web/aframe/8frame-0.9.0.min.js' },
        { src: '//cdn.8thwall.com/web/xrextras/xrextras.js' },
        { src: '//apps.8thwall.com/xrweb?appKey=z1PVjAcyeuxj4mgjn4lp9aDlAiiiEUBtBvMZaw8Lw8RI98sLKdkzab2UI1YWXWOV2cmSOO', async: true, defer: true }
      ]
    };
  }
};
</script>

<style lang="postcss" scoped>
</style>
