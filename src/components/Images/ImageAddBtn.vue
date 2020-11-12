<template>
  <v-dialog v-model="dialog" max-width="600px">
    <template v-slot:activator="{ on, attrs }">
      <v-btn
        class="mx-2"
        fab
        dark
        small
        color="teal accent-4"
        v-bind="attrs"
        v-on="on"
      >
        <v-icon dark> mdi-plus </v-icon>
      </v-btn>
    </template>
    <v-card>
      <v-card-title>
        <span class="headline">Subir Imagen</span>
      </v-card-title>
      <v-card-text>
        <v-container>
          <v-row>
            <v-col cols="12" sm="8">
              <v-text-field
                label="Title*"
                placeholder="Title"
                v-model="newTitle"
                required
              ></v-text-field>
            </v-col>
            <v-col cols="12">
              <v-file-input
                label="Image*"
                :rules="ImgUploadrules"
                accept="image/png, image/jpeg, image/bmp"
                placeholder="Upload your image"
                prepend-icon="mdi-camera"
                v-model="newFile"
              ></v-file-input>
            </v-col>
            <v-col cols="12">
              <v-textarea v-model="newDescription">
                <template v-slot:label>
                  <div>Descripción</div>
                </template>
              </v-textarea>
            </v-col>
          </v-row>
        </v-container>
        <small>*indicates required field</small>
      </v-card-text>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn color="blue darken-1" text @click="dialog = false">
          Close
        </v-btn>
        <v-btn
          color="blue darken-1"
          text
          @click="
            EmitUploadEvent();
            dialog = false;
          "
        >
          Save
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  name: "ImageAddBtn",
  data: () => ({
    dialog: false,
    ImgUploadrules: [
      (value) =>
        !value ||
        value.size < 2000000 ||
        "Avatar size should be less than 2 MB!",
    ],
    newTitle: "",
    newDescription:"",
    newFile: {}
  }),
  methods: {
    EmitUploadEvent() {
      let newTitle = this.newTitle;
      let newFile = this.newFile;
      let newDescription = this.newDescription;
      this.$emit('uploadFile',newFile,newTitle,newDescription);
    },
  },
};
</script>
