<script setup>
import { defineProps } from 'vue';

const p = defineProps({
  isWithColor: Boolean
})

const copyUrl = (url) => {
  navigator.clipboard.writeText(url)
}
</script>
<template>
  <v-card class="mx-5 my-2">
    <v-row>
    <v-col 
      v-for="n in 200"
      cols="4"
      sm="3"
      md="2"
      lg="1"
      :key="n"
      >
      <v-card :elevation="isHovering ? 12 : 2" v-bind="props" @click="copyUrl(`https://picsum.photos/500/300?image=${n * 5 + 10}${p.isWithColor ? '' : '&grayscale'}`)">
        <v-img
        :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}${p.isWithColor ? '' : '&grayscale'}`"
        :src="`https://picsum.photos/500/300?image=${n * 5 + 10}${p.isWithColor ? '' : '&grayscale'}`"
        aspect-ratio="1"
        class="bg-grey-lighten-2"
        cover
      >
        <template v-slot:placeholder>
          <v-row
            align="center"
            class="fill-height ma-0"
            justify="center"
          >
            <v-progress-circular
              color="grey-lighten-5"
              indeterminate
            ></v-progress-circular>
          </v-row>
        </template>
      </v-img>
      </v-card>
    </v-col>
  </v-row>
  </v-card>
</template>