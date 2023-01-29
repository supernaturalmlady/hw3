<template>
  <div class="post">
    <div :style="{ backgroundColor: selectedBackground }">
      <div>
        <strong contenteditable="true" @input="updateTitle">{{
          post.title
        }}</strong>
      </div>
      <div
        :style="{
          fontFamily: selectedFont,
          fontStyle: selectedStyle,
          fontWeight: selectedWeight,
          color: selectedColor,
        }"
        contenteditable="true"
        @input="updateBody"
        class="post-body"
      >
        {{ post.body }}
      </div>
    </div>
    <div class="post-buttons">
      <div>
        <div>Font:</div>
        <select v-model="selectedFont">
          <option v-for="font in fonts" :value="font" :key="font">
            {{ font }}
          </option>
        </select>

        <div>Style:</div>
        <select v-model="selectedStyle">
          <option v-for="style in styles" :value="style" :key="style">
            {{ style }}
          </option>
        </select>

        <div>Weight:</div>
        <select v-model="selectedWeight">
          <option v-for="weight in weights" :key="weight" :value="weight">
            {{ weight }}
          </option>
        </select>

        <div>Color:</div>
        <select v-model="selectedColor">
          <option v-for="color in colors" :value="color" :key="color">
            {{ color }}
          </option>
        </select>

        <div>Background:</div>
        <select v-model="selectedBackground">
          <option
            v-for="background in backgrounds"
            :value="background"
            :key="background"
          >
            {{ background }}
          </option>
        </select>

        <div>Text with selected styles</div>
      </div>
      <button class="btn" @click="$emit('remove', post)">Delete</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedFont: 'Arial',
      fonts: ['Arial', 'Times New Roman', 'Courier New'],
      selectedStyle: 'normal',
      styles: ['normal', 'italic', 'oblique'],
      selectedWeight: 'normal',
      weights: ['normal', 'bold', 'bolder', 'lighter'],
      selectedColor: 'black',
      colors: ['black', 'red', 'green', 'blue'],
      selectedBackground: 'white',
      backgrounds: ['white', 'green', 'gray', 'skyblue'],
    }
  },
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
  methods: {
    updateTitle(event) {
      this.post.title = event.target.innerText
    },
    updateBody(event) {
      this.post.body = event.target.innerText
    },
  },
}
</script>

<style scoped>
.post-body {
  white-space: pre-line;
}
.post {
  border: 3px solid skyblue;
  padding: 15px;
  margin-top: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.post-buttons {
  display: flex;
  flex-direction: column;
  align-items: center;
}
select {
  width: 100px;
  margin-bottom: 10px;
}
</style>
