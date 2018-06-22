<template>
  <div id="app">
    <tabs v-model="activeTab">
      <div
        v-for="(tab, i) in tabs"
        :key="i"
        :tab="tab"
        :style="{ background: tab }"
      >
        Tab: {{tab}}
      </div>
    </tabs>
  </div>
</template>

<script>
import Tabs from './Tabs';

export default {
  name: 'App',
  components: {
    Tabs,
  },
  data() {
    return {
      tabs: ['red', 'green', 'blue'],
      activeTab: 'blue',
    };
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
