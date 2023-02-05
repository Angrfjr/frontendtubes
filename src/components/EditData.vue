<template>
  <div>
    <TheNavbar/>
   <div class="container mx-auto mt-5 row col-md-12 card border-0 bg-gray-900 rounded shadow">
      <div class="card-body text-white px-2 py-2">
        <h1 class="bg-gray-700 rounded-md mb-4 text-4xl text-center font-mono Liberation Mono leading-none tracking-tight text-white font-bold px-3 py-2 md:text-4xl lg:text-4xl dark:text-white">UPDATE DATA MAHASISWA</h1>
      <div class="field">
          <div class="mb-6">
            <label for="default-input" class="block mb-2 text-xl font-medium text-white dark:text-white">Nama</label>
            <input 
            type="text" 
            id="default-input" 
            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
            v-model="nama"
            >
          </div>
      </div>
      <div class="field">
          <div class="mb-6">
            <label for="default-input" class="block mb-2 text-xl font-medium text-white dark:text-white">Umur</label>
            <input 
            type="text" 
            id="default-input" 
            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
            v-model="umur"
            >
          </div>
      </div>
      <div class="field">
          <div class="mb-6">
            <label for="default-input" class="block mb-2 text-xl font-medium text-white dark:text-white">NIM</label>
            <input 
            type="text" 
            id="default-input" 
            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
            v-model="nim"
            >
          </div>
      </div>
      <div class="field">
          <div class="mb-6">
            <label for="default-input" class="block mb-2 text-xl font-medium text-white dark:text-white">Alamat</label>
            <input 
            type="text" 
            id="default-input" 
            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
            v-model="alamat"
            >
          </div>
      </div>
      <div class="field">
          <div class="mb-6">
            <label for="default-input" class="block mb-2 text-xl font-medium text-white dark:text-white">Prodi</label>
            <input 
            type="text" 
            id="default-input" 
            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
            v-model="prodi"
            >
          </div>
      </div>
      <div class="control">
        <button type="button" class="text-white bg-gradient-to-r from-green-400 via-green-500 to-green-600 hover:bg-gradient-to-br focus:ring-4 focus:outline-none focus:ring-green-300 dark:focus:ring-green-800 font-medium rounded-lg text-sm px-5 py-2.5 text-center mr-2 mb-2" @click="updateUsers">Update</button>
      </div>
    </div>
   </div>
  </div>
  </template>
   
  <script>
  // import axios
  import axios from "axios";
  import TheNavbar from "./TheNavbar.vue";
  
   
  export default {
    name: "EditData",
    components: {
      TheNavbar
    },
    data() {
      return {
        nama: "",
        umur: "",
        nik: "",
        alamat: "",
        status: "",
      };
    },
    created: function () {
      this.getUsersById();
    },
    methods: {
      // Get Product By Id
      async getUsersById() {
        try {
          const response = await axios.get("http://localhost:5000/users/${this.$route.params.id}");
          this.nama = response.data.nama;
          this.umur = response.data.umur;
          this.nim = response.data.nim;
          this.alamat = response.data.alamat;
          this.prodi = response.data.prodi; 
        } catch (err) {
          console.log(err);
        }
      },
   
      // Update product
      async updateUsers() {
      try {
        await axios.patch(
          `http://localhost:5000/users/${this.$route.params.id}`,
          {
            nama: this.nama,
            umur: this.umur,
            nim: this.nim,
            alamat: this.alamat,
            prodi: this.prodi,
          }
        );
        this.nama = "";
        this.umur = "";
        this.nim = "";
        this.alamat = "";
        this.prodi = "";
        this.$router.push("/");
      } catch (err) {
        console.log(err);
      }
    },
    },
  };
  </script>
   
  <style>
  </style>