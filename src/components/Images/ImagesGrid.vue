<template>
  <v-row>
    <v-col
      v-for="image in images"
      :key="image.id"
      class="d-flex child-flex col-sm-9 col-sm-6 col-md-5 col-lg-3"
    >
      <v-card :loading="loading" class="mx-auto my-auto" max-width="374">
        <template slot="progress">
          <v-progress-linear
            color="deep-purple"
            height="10"
            indeterminate
          ></v-progress-linear>
        </template>

        <v-img
          height="250"
          :src="`http://localhost:3000` + image.url"
          :lazy-src="`http://localhost:3000` + image.url"
          aspect-ratio="1"
          class="grey lighten-2"
        ></v-img>

        <v-card-title>{{image.title || "Café Comodin"}}</v-card-title>

        <v-card-text>
          <div>
           {{image.description}}
          </div>
        </v-card-text>

        <v-divider class="mx-4"></v-divider>

        <v-card-actions>
           <v-spacer></v-spacer>
          <v-btn @click="DeleteFile(image.id, image.url)" class="mx-2" fab dark small color="red">
            <v-icon dark> mdi-delete </v-icon>
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
import { HTTP } from "../../helpers/axiosconfig";

export default {
  name: "ImagesGrid",
  data() {
    return {
      loading: false,
      images: []
    }
  },
  methods: {
    DeleteFile(id,url) {
      if (id && url) {
        HTTP.delete("api/images/delete/" + id, {data:{
          url
        }});
      }
    },
  },
  mounted() {
    HTTP.get("api/images/")
    .then(res =>this.images = res.data);
  }
};
</script>
