<template>
  <div class="home">
    <A />
    <Com />
    <h2>insert name slot</h2>
    <slot name="insert"></slot>
    <input v-model="text" />

    <h2>scoped name slot</h2>
    <slot name="aabb" :text="text">
      <div>aabb</div>
    </slot>
    <input v-model="text" />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Com from "./Com";

export default Vue.extend({
  name: "Home",
  components: {
    Com,
    A: Vue.extend({
      render(h) {
        return h("div", undefined, "From A");
      },
    }),
  },
  watch: {
    text: {
      deep: true,
      handler(nv) {
        const h = this.$createElement;
        const vnode = h("div", {}, [nv]);
        // debugger;
        this.$slots.insert = [vnode];

        console.log(this);
        //debugger;
        // this.$scopedSlots.aabb = (text: string) => {
        //   return [vnode];
        // };
      },
    },
  },
  data() {
    const text = "hello world";
    return {
      text,
    };
  },
  mounted() {
    console.log(this);
  },
});
</script>
