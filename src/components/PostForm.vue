<template>
  <form @submit.prevent>
    <h1>Create a post</h1>
    <input
      v-model="post.title"
      class="input"
      type="text"
      placeholder="Post name"
    />
    <textarea
      v-model="post.body"
      class="input"
      type="text"
      placeholder="Post text"
    />
    <h3 v-if="showError">Enter your post</h3>
    <button @click="createPost" class="btn">Create</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: '',
        body: '',
      },
      showError: true,
    }
  },

  methods: {
    createPost() {
      if (this.post.title.length && this.post.body.length >= 5) {
        this.showError = false
        this.post.id = Date.now()
        this.$emit('create', this.post)
        this.post = {
          title: '',
          body: '',
        }
      }
    },
  },
}
</script>

<style>
form {
  display: flex;
  flex-direction: column;
}

.btn {
  align-self: flex-end;
  margin-top: 10px;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
}

.input {
  width: 100%;
  border: 1px solid skyblue;
  padding: 10px 15px;
  margin-top: 10px;
}

h3 {
  color: red;
  text-align: right;
  margin-top: 10px;
}

textarea {
  resize: none;
}
</style>
