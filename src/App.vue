<template>
  <div>
    <Backtop>
      <router-view></router-view>
    </Backtop>
  </div>
</template>
<script>
import Backtop from "../src/components/Backtop";
export default {
  components: {
    Backtop
  }
};
</script>

<style lang="scss">
@import "../src/styles/common";
* {
  margin: 0;
  padding: 0;
}

a {
  color: black;
  text-decoration: none;
}
ul {
  list-style: none !important;
}
</style>
