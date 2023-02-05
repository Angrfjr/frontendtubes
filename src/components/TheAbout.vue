<template>
  <div>
    <TheNavbar />
    <figure class="relative bg-auto">
      <img class="rounded-lg opacity-50" src="../assets/telkom5.jpg" alt="Telkom Image">
      <figcaption class="absolute px-4 py-4 text-lg text-white top-6">
        <h1
          class="mb-3 text-7xl font-extrabold tracking-tight text-gray-900 dark:text-white">
          <center>We are here for Helping Student Data</center>
        </h1>
        <span class="m-2"></span>
        <p class="mb-3 text-3xl font-sans font-medium text-gray-100 dark:text-gray-400">
          <center>Telkom Dikti merupakan Aplikasi buatan kelompok kami yang memiliki fungsi dalam Pencatatan Data Mahasiswa secara simpel dan mudah untuk digunakan oleh
            semua orang.</center>
        </p>
        <span class="m-2"></span>
        <a href="https://pddikti.kemdikbud.go.id/"
          class="bottom-6 inline-flex items-center justify-center px-5 py-3 text-base font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 dark:focus:ring-blue-900">
          Learn more
          <svg class="w-5 h-5 ml-2 -mr-1" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
            <path fill-rule="evenodd"
              d="M10.293 3.293a1 1 0 011.414 0l6 6a1 1 0 010 1.414l-6 6a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-4.293-4.293a1 1 0 010-1.414z"
              clip-rule="evenodd"></path>
          </svg>
        </a>
      </figcaption>
    </figure>
  </div>
</template>
  
<script>
import TheNavbar from './TheNavbar.vue';
export default {
  nama: "TheAbout",
  components: {
    TheNavbar
  }
}
</script>
  
<style>

</style>