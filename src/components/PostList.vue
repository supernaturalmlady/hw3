<template>
  <div v-if="posts.length > 0">
    <h2>Post list</h2>
    <PostItem
      v-for="post of posts"
      :key="post.id"
      :post="post"
      @remove="$emit('remove', post)"
    />
  </div>
  <h2 v-else>Post list is empty</h2>
</template>

<script>
import PostItem from '@/components/PostItem.vue'

export default {
  components: {
    PostItem,
  },

  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
}
</script>

<style></style>
