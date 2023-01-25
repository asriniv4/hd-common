<script setup>
import { defineProps, ref, onMounted, toRefs } from 'vue';  
import axios from 'axios';

const props = defineProps({
  recentCase: {
    type: Object,
    required: true,
  }
});
const { recentCase } = toRefs(props);

console.log(recentCase.value.thumbnail_location)

const name = recentCase.value.thumbnail_location;
const GET_THUMBNAIL_URL = `https://common.ismorebetter.com/.netlify/functions/get-thumbnail-url?name=${name}`;

const thumbnailUrl = ref(null);
const loading = ref(true);

onMounted(() => {
  axios.get(GET_THUMBNAIL_URL)
    .then((response) => {
      console.log(response);
      thumbnailUrl.value = response.data;
      loading.value = false;
    })
    .catch((error) => {
      console.log(error);
      loading.value = false;
    });
});
</script>

<template>
  <div class="col">
    <div class="card shadow-sm">
      <div class="card-body">
        <p>{{ recentCase.description }}</p>
        <div v-if="loading" class="d-flex justify-content-center">
          <div class="spinner-border text-info" role="status">
            <span class="visually-hidden">Loading...</span>
          </div>  
        </div>
        <a v-else :href="recentCase.video_url">
          <img class="thumbnail" :src="thumbnailUrl" />
        </a>
        <div><strong>Primary:&nbsp;</strong>{{ recentCase.primary_surgeon }}</div>
        <div><strong>Secondary:&nbsp;</strong>{{  recentCase.secondary_surgeon }}</div>
      </div>
    </div>
  </div>
</template>

<style scoped>
img.thumbnail {
  width: 100%
}
</style>