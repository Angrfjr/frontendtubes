<template>
    <div class="mx-auto">
      <TheNavbar/>
      <h1 class="bg-gray-700 mb-4 text-4xl text-center font-mono Liberation Mono leading-none tracking-tight text-white font-bold px-2 py-1 md:text-4xl lg:text-4xl dark:text-white">LIST DATA</h1>
      <div class="container mx-auto mt-5 row col-md-12 card border-0 bg-gray-900 shadow">
            <table class="w-full rounded-lg text-sm text-left text-blue-100 dark:text-blue-100">
                <thead class="text-xs text-white uppercase bg-gray-800 border-b border-gray-400 dark:text-white">
                    <tr>
                        <th scope="col" class="text-center px-6 py-3">Nama</th>
                        <th scope="col" class="text-center px-6 py-3">Umur</th>
                        <th scope="col" class="text-center px-6 py-3">NIM</th>
                        <th scope="col" class="text-center px-6 py-3">Alamat</th>
                        <th scope="col" class="text-center px-6 py-3">Prodi</th>
                        <th scope="col" class="text-center px-6 py-3">Actions</th>
                    </tr>
                </thead>
                <tbody>
                    <tr class="bg-gray-600 border-b border-gray-400 hover:bg-gray-400" v-for="item in items" :key="item.id">
                        <th scope="row" class="text-center px-6 py-4 font-medium text-blue-50 whitespace-nowrap dark:text-blue-100">{{ item.nama }}</th>
                        <td class="text-center px-6 py-4">{{ item.umur }}</td>
                        <td class="text-center px-6 py-4">{{ item.nim }}</td>
                        <td class="text-center px-6 py-4">{{ item.alamat }}</td>
                        <td class="text-center px-6 py-4">{{ item.prodi }}</td>
                        <td class="text-center px-6 py-4">
                          <router-link
                            :to="{ name: 'Edit', params: { id: item.id } }"
                            class="button is-info bg-blue-600 rounded px-2 py-1 text-white hover:bg-red-400"
                            >Update</router-link>
                          <span class="mx-1"></span>
                          <a
                            type="button" class="button is-success bg-red-600 rounded px-2 py-1 text-white hover:bg-red-400"
                            href=# @click="deleteUsers(item.id)"
                            >Delete</a>
                        </td>
                      </tr>
                </tbody>
            </table>
        </div>
  </div>
  </template>
   
  <script>
  // import axios
  import axios from "axios";
  import TheNavbar from "./TheNavbar.vue";


  export default {
    name: "DataList",
    components: {
      TheNavbar
    },
    data() {
      return {
        items: [],
      };
    },
   
    created() {
      this.getUsers();
    },
   
    methods: {
      // Get All Products
      async getUsers() {
        try {
          const response = await axios.get("http://localhost:5000/users");
          this.items = response.data;
        } catch (err) {
          console.log(err);
        }
      },
   
      // Delete Product
      async deleteUsers(id) {
        try {
          await axios.delete(`http://localhost:5000/users/${id}`);
          this.getUsers();
        } catch (err) {
          console.log(err);
        }
      },
    },
  };
  </script>
   
  <style>
  </style>
