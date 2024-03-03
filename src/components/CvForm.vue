<script>
import Icon from '@/components/Icon.vue'
import { QuillEditor } from '@vueup/vue-quill'
import '@vueup/vue-quill/dist/vue-quill.snow.css'

export default {
  components: { Icon, QuillEditor },
  data() {
    return {
      formData: {
        image: 'image1',
        company: 'Coop',
        position: 'Ostujuhti',
        description:
          "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s",
        telefon: '54593232',
        email: 'testemail@hotmail.com',
        offers: ['Vegetables', 'Cheese', 'Whatever else'],
        suitableCandidate:
          '<ul><li>Lorem Ipsum is simply dummy text of the printing and</li><li>Lorem Ipsum is simply dummy text of the printing and</li><li>Lorem Ipsum is simply dummy text of the printing and</li></ul>',
        checked: true
      },
      textareaContent: ''
    }
  },
  created() {
    this.textareaContent = this.formData.offers.join('\n')
    this.updateFormData()
  },
  methods: {
    updateFormData() {
      this.$emit('form-updated', this.formData)
      this.formData.offers = this.textareaContent.split('\n')
    }
  }
}
</script>

<template>
  <div>
    <h6 class="header text-lg dark:text-white mb-12">Koosta töökuulutus</h6>
    <div>
      <label for="foto" class="block mb-2">Foto</label>
      <div class="relative">
        <select
          id="small"
          v-model="formData.image"
          @change="updateFormData"
          class="input-global block w-full p-2 pr-8 mb-6"
        >
          <option value="" disabled selected hidden>Choose a country</option>
          <option value="image1">Kassatöötaja</option>
          <option value="image2">Kontoritöötaja</option>
        </select>
        <icon class="absolute inset-y-0 inset-x-auto top-4 right-4" name="dropdown" />
      </div>
    </div>
    <div>
      <label for="company" class="block mb-2">Kes otsib?</label>
      <div class="relative">
        <select
          id="small"
          v-model="formData.company"
          @change="updateFormData"
          class="input-global block w-full p-2 pr-8 mb-6"
        >
          <option value="" disabled selected hidden>Choose a country</option>
          <option value="Coop">Coop</option>
          <option value="Swedbank">Swedbank</option>
        </select>
        <icon class="absolute inset-y-0 inset-x-auto top-4 right-4" name="dropdown" />
      </div>
    </div>
    <div>
      <div class="flex justify-between">
        <label for="position" class="block mb-2">Keda otsib?</label>
        <p class="maxLength">60 tähemärki</p>
      </div>
      <input
        v-model="formData.position"
        type="text"
        id="position"
        class="w-inputField input-global h-customHeight mb-8"
        placeholder="Keda otsib?"
        maxlength="60"
        required
      />
    </div>
    <div>
      <div class="flex justify-between">
        <label for="description" class="block mb-2">Töö lühikirjeldus</label>
        <p class="maxLength">120 tähemärki</p>
      </div>
      <textarea
        v-model="formData.description"
        id="description"
        class="resize-none input-global w-inputField rounded-md h-[5.438rem] mb-8"
        placeholder="Töö lühikirjeldus"
        @input="updateFormData"
        maxlength="120"
      ></textarea>
    </div>
    <div class="mb-2">
      <label class="container"
        >Pakkumised
        <input @change="updateFormData" v-model="formData.checked" type="checkbox" />
        <span class="checkmark"></span>
      </label>
    </div>

    <div v-if="formData.checked">
      <textarea
        v-model="textareaContent"
        id="offers"
        class="input-global resize-none input-global w-inputField rounded-md h-[5.438rem] mb-8"
        placeholder=""
        @change="updateFormData"
      >
      </textarea>
    </div>
    <div class="w-inputField mb-2">
      <QuillEditor v-model:content="formData.suitableCandidate" contentType="html"></QuillEditor>
    </div>

    <div>
      <label for="kontakt" class="block mb-2">Kontakt</label>
      <input
        v-model="formData.email"
        type="text"
        id="kontakt"
        class="w-inputField input-global h-customHeight mb-8"
        placeholder="Kontakt"
        required
      />
    </div>

    <div>
      <input
        v-model="formData.telefon"
        type="number"
        id="telefon"
        class="w-inputField input-global h-customHeight mb-8"
        placeholder="Telefon"
        required
      />
    </div>
  </div>
</template>
