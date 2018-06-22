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
import { object } from 'super-helpers';

export default {
  name: 'Tabs',
  props: ['value'],
  computed: {
    tabButtonList() {
      const tab = this.value;
      return this.$slots.default
        .filter(child => {
          //filter if do not have the "tab" atribute
          return object.getFlattened('data.attrs.tab', child, false);
        })
        .map(child => {
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
      this.$emit('input', v);
    },
  },
};
</script>
<style lang="stylus">
.tab
  color #fff
  padding 10px
  display none

.active
  display block

</style>
