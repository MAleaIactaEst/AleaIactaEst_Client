<template>
  <v-container fluid>
    <v-row>
      <v-col class=" col-sm-5 col-md-3 col-lg-2">
        <ImagesMenu/>
      </v-col>
      <v-col>
          <ImageBar/>
          <ImagesGrid/>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
// @ is an alias to /
import ImagesMenu from '@/components/Images/ImagesMenu.vue'
import ImagesGrid from '@/components/Images/ImagesGrid.vue'
import ImageBar from '@/components/Images/ImageBar.vue'

export default {
  name: 'Images',
  components: {
    ImagesMenu,
    ImagesGrid,
    ImageBar
  },
  data () {
      return {
        items: [
          { title: 'Home', icon: 'mdi-view-dashboard' },
          { title: 'About', icon: 'mdi-forum' },
        ],
      }
    },
}
</script>
