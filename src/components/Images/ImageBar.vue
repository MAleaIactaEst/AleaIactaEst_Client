<template>
  <v-container fluid class="pa-0">
    <v-app-bar dense flat color="transparent">
      <v-spacer></v-spacer>
      <ImageAddBtn @uploadFile="uploadFile"/>
    </v-app-bar>
  </v-container>
</template>

<script>
import ImageAddBtn from '@/components/Images/ImageAddBtn.vue'
import { HTTP } from "../../helpers/axiosconfig";

export default {
  name: "ImageBar",
  components: {
    ImageAddBtn
  },
  methods: {
    uploadFile(newFile,newTitle,newDescription) {
      if (newFile) {
        const formData = new FormData();
        formData.append('title',newTitle);
        formData.append('description',newDescription);
        formData.append('file',newFile);
        
        HTTP.post(
          "api/images/upload",formData);
      }
    },
  },
};
</script>
