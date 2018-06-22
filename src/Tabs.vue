<template>
  <div>
  <div>
    <slot/>
  </div>
  <button
    v-for="(value, key) in tabButtonList"
    :key="key"
    @click="setTab(value)"
  >
  {{ value }}
  </button>
  </div>
</template>

<script>
export default {
  name: 'Tabs',
  props: ['value'],
  computed: {
    tabButtonList() {
      const tab = this.value;
      return this.$slots.default.map(child => {
        child.data.class = [
          'tab',
          {
            active: child.data.attrs.tab === tab,
          },
        ];
        return child.data.attrs.tab;
      });
    },
  },
  methods: {
    setTab(v) {
      console.log(v);
      this.$emit('input', v);
    },
  },
};
</script>
<style lang="stylus">
.tab
  color #fff
  padding: 10px
  display none

.active
  display block

</style>
