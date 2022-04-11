<template>
  <div>
    <app-menu/>
    <app-articles/>
  </div>
</template>
<script>
import Menu from "../components/Menu";
import Articles from "../components/Articles";

export default {
  components: {
    'app-menu': Menu,
    'app-articles' : Articles
  }
}
</script>

