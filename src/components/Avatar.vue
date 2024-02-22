<template>
  <img
    class="user_avatar"
    :src="url"
    :style="{ width: size + 'px', height: size + 'px' }"
  />
</template>

<script>
export default {
  props: {
    url: {
      type: String,
      require: true,
    },
    size: {
      type: Number,
    },
  },
};
</script>

<style>
.user_avatar {
  border-radius: 50%;
  object-fit: cover;
  display: block;
}
</style>
