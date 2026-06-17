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
      <div>
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
            <p>No selected file...</p>
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
  gap: 8px;
  font-family: Roboto;
}
.title {
  text-align: left;
  font-weight: 600;
  font-size: 22px;
}
.reviewForm h3 {
  width: 50%;
  margin: 0 0 0 0;
  align-self: flex-start;
  font-weight: 600;
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
  border-radius: 8px;
  border: 1px solid darkgray;
}
.reviewTitleBox input {
  height: 50px;
  font-size: large;
}
.reviewBox textarea {
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
.chooseFile p{
  font-weight: 600;
  color: darkgrey;
}
.chooseFile button {
  height: 50px;
  font-size: 15px;
  font-weight: 600;
  border-radius: 4px;
  border-width: 0.5px;
}
.buttonBox {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}
.buttonBox button {
  width: 100%;
  height: 50px;
  border-radius: 30px;
  border-width: 0;
  background-color: #0671ba;
  color: #ffffff;
  font-weight: 600;
  font-size: large;
}

@media (max-width: 1024px) {
  .box {
    width: 100%;
    position: static;
    justify-content: stretch;
  }

  .reviewForm {
    width: 100%;
    padding: 20px 24px;
  }
}

@media (max-width: 768px) {
  .reviewForm {
    padding: 16px;
  }

  .title {
    font-size: 20px;
  }

  .reviewTitleBox input,
  .reviewBox textarea,
  .chooseFile button,
  .buttonBox button {
    height: auto;
    min-height: 48px;
  }

  .chooseFile {
    flex-direction: column;
    align-items: stretch;
    gap: 12px;
  }

  .buttonBox button {
    padding: 12px 16px;
  }
}
</style>
