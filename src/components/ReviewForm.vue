<script setup lang="ts">
import StarRating from "./StarRating.vue";
import { reactive, ref } from "vue";

type ReviewForm = {
  title: string;
  rating: number;
  review: string;
  image: File | null;
};

const form = reactive<ReviewForm>({
  title: "",
  rating: 0,
  review: "",
  image: null,
});

const fileInput = ref<HTMLInputElement | null>(null);
const selectedFile = ref<string>("No selected file...");

function openFilePicker() {
  fileInput.value?.click();
}

function handleFileChange(event: Event) {
  const input = event.target as HTMLInputElement;
  if (input.files && input.files.length > 0) {
    form.image = input.files[0];
    selectedFile.value = input.files[0].name;
  } else {
    form.image = null;
    selectedFile.value = "No selected file...";
  }
}
</script>

<template>
  <section class="box">
    <div class="reviewForm">
      <h2 class="title">Submit Your Review</h2>
      <div class="reviewTitleBox">
        <label for="review-title"
          >Review Title<span class="required" aria-hidden="true">*</span></label
        >
        <input
          type="text"
          id="review-title"
          v-model="form.title"
          maxlength="60"
        />
      </div>
      <div role="group" aria-labelledby="rate-label">
        <label id="rate-label"
          >Rate<span class="required" aria-hidden="true">*</span></label
        >
        <StarRating v-model="form.rating" />
      </div>
      <div class="reviewBox">
        <label for="review-body"
          >Review<span class="required" aria-hidden="true">*</span></label
        >
        <textarea
          id="review-body"
          v-model="form.review"
          maxlength="2000"
        ></textarea>
      </div>
      <div class="addImageBox">
        <label>Add Image<span class="optional">(optional)</span></label>
        <div class="upload-container">
          <div class="chooseFile">
            <input
              type="file"
              ref="fileInput"
              id="file-upload"
              aria-label="Upload image"
              style="display: none"
              @change="handleFileChange"
            />
            <button
              type="button"
              @click="openFilePicker"
              aria-controls="file-upload"
            >
              Select Files
            </button>
            <p aria-live="polite">{{ selectedFile }}</p>
          </div>
        </div>
      </div>
      <div class="buttonBox">
        <button type="submit">Submit Review</button>
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
  top: 1rem;
  font-family:
    system-ui,
    -apple-system,
    BlinkMacSystemFont,
    "Segoe UI",
    Roboto,
    Oxygen,
    Ubuntu,
    Cantarell,
    "Open Sans",
    "Helvetica Neue",
    sans-serif;
}
.reviewForm {
  background-color: #f5f5f5;
  width: 70%;
  padding: 24px 40px;
  border-radius: 8px;
  display: flex;
  flex-direction: column;
  gap: 4px;
}
.title {
  font-weight: 700;
  font-size: 22px;
}
.reviewForm h3,
.reviewForm label {
  margin: 0;
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
  border: 1px solid rgb(207, 207, 207);
}
.reviewTitleBox input {
  height: 50px;
  font-size: large;
}
.reviewBox textarea {
  font-size: medium;
  min-height: 150px;
  max-height: 300px;
  resize: vertical;
}
.chooseFile {
  display: flex;
  align-items: center;
  width: 100%;
  gap: 20px;
  border-radius: 8px;
  border: 1px solid rgb(207, 207, 207);
  background-color: white;
  padding: 5px;
}
.chooseFile p {
  font-weight: 600;
  color: #595959;
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
  border: none;
  background-color: #0671ba;
  color: #ffffff;
  font-weight: 600;
  font-size: large;
}
.required {
  color: #c0392b;
  margin-left: 2px;
}
.optional {
  font-size: 13px;
  font-weight: 400;
  color: #595959;
  margin-left: 4px;
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
