<template>
  <div class="home">
    <Sms>
      <div>pppp</div>
      <template #aabb="{ text }">
        <div>{{ text }}</div>
      </template>
    </Sms>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Sms from "./Sms";

export default Vue.extend({
  name: "Home",
  components: {
    Sms,
  },
});
</script>
