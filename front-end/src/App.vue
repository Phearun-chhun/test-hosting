<template>
  <form-view @add-Book="addNewBook"></form-view>
  <card-view v-for="(book,index) in books" :key="index" :book="book" @delete-book="deleteBooks"></card-view>
</template>

<script>
import FormView from "./components/FormView.vue";
import CardView from "./components/CardView.vue";
import axios from "axios"
export default {
  name: 'App',
  components: {
    "form-view": FormView,
    "card-view": CardView,
  },
  data() {
    return {
      books: [],
      url: "http://127.0.0.1:8000/api/books",
    }
  },
  methods: {
    getBook() {
      axios.get(this.url).then((response) => {
        this.books = response.data;
        console.log(this.books);
     }) 
    },
    addNewBook(object) {
      axios.post(this.url, object).then(response => {
        console.log(response.data);
        this.getBook();
      }
      )
    },
    deleteBooks(id) {
      // console.log(id)
      axios.delete(this.url+"/"+ id).then(response => {
        this.getBook();
        console.log(response.data);
      })
    }
  },
  mounted() {
    this.getBook();
  }
}
</script>

<style>
#app {
  margin-top: 18%;
}
</style>
