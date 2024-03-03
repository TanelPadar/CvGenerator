<script>
import CvPreview from '@/components/CvPreview.vue'
import CvForm from '@/components/CvForm.vue'
import '../assets/scss/global.scss'

export default {
  name: 'CvGenerator',
  components: {
    CvForm,
    CvPreview
  },
  data() {
    return {
      formData: {}
    }
  },
  methods: {
    handleFormSubmitted(formData) {
      this.formData = formData
    }
  }
}
</script>

<template>
  <header>
    <nav
      class="relative flex w-full mb-10 mx-auto flex-wrap items-center justify-between bg-[#0078D2] py-2 text-neutral-500 shadow-lg hover:text-neutral-700 focus:text-neutral-700 lg:py-4 m-w-[37.5rem]"
    >
      <div class="px-3 w-full">
        <div class="flex items-center justify-between">
          <div class="flex-shrink-0">
            <a class="text-white font-sans text-2xl font-semibold leading-9" href="#"
              >Töökuulutuse generaator</a
            >
          </div>
        </div>
      </div>
    </nav>
  </header>

  <div class="grid grid-cols-1 xl:grid-cols-2 gap-2">
    <div class="flex flex-row justify-center mt-16 ml-20">
      <CvForm @form-updated="handleFormSubmitted" />
    </div>
    <CvPreview :formData="formData" />
  </div>
  <footer
    class="flex flex-row justify-center items-center bg-[#FAFAFA] mt-12 py-4 text-[#979797] h-[9.875rem] m-w-[50rem]"
  >
    <p>&copy; Copyright 2024</p>
  </footer>
</template>
