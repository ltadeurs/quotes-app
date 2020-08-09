<template>
  <div class="footer">
    <p class="copyright">{{ copyright }}</p>
  </div>
</template>

<script>
export default {
  name: "Footer",
  props: {
    copyright: String,
  },
};
</script>