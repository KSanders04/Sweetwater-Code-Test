<script setup lang="ts">
import StarRating from "./StarRating.vue";
import { ref } from "vue";

const myScore = ref(0);
</script>

<template>
  <section class="box">
    <div class="reviewForm">
      <h2 class="title">Submit Your Review</h2>
      <div class="reviewTitleBox">
        <h3>Review Title</h3>
        <input />
      </div>
      <div class="rate">
        <h3>Rate</h3>
        <StarRating v-model="myScore" />
      </div>
      <div class="reviewBox">
        <h3>Review</h3>
        <textarea></textarea>
      </div>
      <div class="addImageBox">
        <h3>Add Image</h3>
        <div class="upload-container">
          <div class="chooseFile">
            <input type="file" ref="fileInput" style="display: none" />
            <button>Select Files</button>
            <p class="file-info">No selected file...</p>
          </div>
        </div>
      </div>
      <div class="buttonBox">
        <button>Submit Review</button>
      </div>
    </div>
  </section>
</template>
<style scoped>
* {
  box-sizing: border-box;
}
.box {
  height: fit-content;
  width: 50%;
  border-radius: 20px;
  display: flex;
  justify-content: end;
  position: sticky;
  top: 3rem;
}
.reviewForm {
  background-color: #f5f5f5;
  width: 65%;
  padding: 24px 40px;
  border-radius: 8px;
  display: flex;
  flex-direction: column;
  font-family: Roboto;
}
.title {
  text-align: left;
  font-weight: 600;
  font-size: 22px;
}
.reviewForm h3 {
  width: 50%;
  margin: 0 0 8px 0;
  align-self: flex-start;
}
.reviewTitleBox,
.reviewBox,
.addImageBox {
  width: 100%;
}
.reviewTitleBox input,
.reviewBox textarea {
  display: block;
  width: 100%;
  padding: 6px 8px;
  margin: 0 0 10px 0;
  border-radius: 8px;
  border: 1 solid darkgray;
}
.reviewTitleBox input {
  height: 50px;
  font-size: large;
}
.reviewBox textarea {
  height: 150px;
  font-size: medium;
  width: 100%;
  min-height: 150px;
  max-height: 300px;
  resize: vertical;
  box-sizing: border-box;
  padding: 5px;
}
.chooseFile {
  display: flex;
  flex-direction: row;
  align-items: center;
  width: 100%;
  gap: 20px;
  background-color: white;
  padding: 5px;
}
.chooseFile button {
  height: 50px;
  font-size: 15px;
  font-weight: 550;
}
.buttonBox {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  margin: 0 auto;
}
.buttonBox button {
  width: 100%;
  height: 50px;
  border-radius: 30px;
  border-width: 0;
  background-color: #0671ba;
  color: #ffffff;
  margin: 10px 0 0 0;
  font-weight: 600;
  font-size: large;
}
.rate {
  margin: 0 0 10px 0;
}
.rate h3 {
  margin: 0 0 0 0;
}
</style>
