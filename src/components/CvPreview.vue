<script>
export default {
  props: {
    formData: {
      type: Object,
      required: true
    }
  },
  methods: {
    getImageSrc(imageType) {
      switch (imageType) {
        case 'image1':
          return 'src/assets/image/girl2.jpeg'
        case 'image2':
          return 'src/assets/image/girl1.jpeg'
        default:
          return 'src/assets/image/girl1.jpeg'
      }
    }
  }
}
</script>

<template>
  <div
    class="flex flex-col background-image-container rounded shadow-2xl flex items-center justify-center p-20 w-[50rem]"
  >
    <div class="flex flex-row justify-start w-full my-12">
      <div><p class="header">Töökuulutuse eelvaade</p></div>
    </div>
    <div class="background-image relative bg-[url('src/assets/image/background-image.png')]">
      <div class="flex flex-row justify-center sm:justify-end">
        <div>
          <img :src="getImageSrc(formData.image)" alt="office worker" />
        </div>
      </div>
      <div class="flex flex-col justify-start space-x-8">
        <div class="flex space-y-2 flex-col mt-5 space-x-8">
          <p></p>
          <p class="text-white text-lg">{{ formData.company }} otsib</p>
          <p class="text-4xl text-white">{{ formData.position }}</p>
          <p class="text-white">
            {{ formData.description }}
          </p>
        </div>
        <div v-if="formData.checked" class="flex flex-col">
          <p class="text-white text-white text-2xl ml-8 mt-5">Pakume sulle</p>
          <ol class="text-white ml-20 mt-2">
            <li class="list-disc" v-for="offer in formData.offers" :key="offer">{{ offer }}</li>
          </ol>
        </div>

        <div class="flex flex-col">
          <p class="text-white text-white text-2xl ml-8 mt-5">Sobiv kandidaat</p>
          <div class="text-white ml-20 mt-2">
            <div class="list-disc" v-html="formData.suitableCandidate"></div>
          </div>
        </div>

        <div class="flex flex-row mt-4 items-center space-x-12 2">
          <div
            class="background-image2 rounded-full w-52 h-44 bg-[url('src/assets/image/konsum.jpeg')]"
          ></div>

          <div class="rounded-full bg-lime-200 p-4">
            <div class="flex gap-1">
              <p class="text-tiny">Saada CV aadressile</p>
              <p class="text-tiny">{{ formData.email }}</p>
            </div>
            <p class="text-tiny">Lisainfo telefonil +372 {{ formData.telefon }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
