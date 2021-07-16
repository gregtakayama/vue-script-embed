<template>
  <div id="app">
    <div id="tradingview"></div>

    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';

export default {
  name: 'App',
  components: {
    HelloWorld,
  },
  mounted() {
    let tvEl = document.getElementById('tradingview');
    let tradingViewScript = document.createElement('script');
    tradingViewScript.setAttribute('src', 'https://s3.tradingview.com/tv.js');
    tvEl.appendChild(tradingViewScript);

    let tradingViewEmbed = document.createElement('script');
    tradingViewEmbed.innerHTML = `
      let tradingview_embed_options = {};
      tradingview_embed_options.width = '1056';
      tradingview_embed_options.height = '600';
      tradingview_embed_options.chart = 'shYXrfrg';
      new TradingView.chart(tradingview_embed_options);
    `;
    tvEl.appendChild(tradingViewEmbed);

    this.$nextTick(() => {
      //   let tradingViewEmbed = document.createElement('script');
      //   tradingViewEmbed.innerHTML = `
      //   let tradingview_embed_options = {};
      //   tradingview_embed_options.width = '1056';
      //   tradingview_embed_options.height = '600';
      //   tradingview_embed_options.chart = 'shYXrfrg';
      //   new TradingView.chart(tradingview_embed_options);
      // `;
    });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
