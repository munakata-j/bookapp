<template>
  <v-app>
    <PageHeader/>
    <v-main>
      <router-view
          @add-book-list="addBook"
      />
    </v-main>
    <PageFooter/>
  </v-app>
</template>

<script>
import PageHeader from "@/global/PageHeader.vue";
import PageFooter from "@/global/PageFooter.vue";

const STORAGE_KEY = 'books';
export default {
  name: 'App',
  components: {
    PageHeader,
    PageFooter
  },

  data() {
    return {
      books: [],
      newBook: null
    }
},
  mounted() {
    if (localStorage.getItem(STORAGE_KEY)) {
      try {
        this.books = JSON.parse(localStorage.getItem(STORAGE_KEY));
      } catch(e) {
        localStorage.removeItem(STORAGE_KEY);
      }
    }
  },
  methods: {
    //引数に「e 」を渡すことでこコンポーネントからデータが渡される
    addBook(e) {
      this.books.push({
        id: this.books.length,
        title: e.title,
        image: e.image,
        description: e.description,
        readDate: '',
        memo: ''
      });
      //this.newBook = '';
      this.saveBooks();
    },
    removeBook(x) {
      this.books.splice(x, 1);
      this.saveBooks();
    },
    saveBooks() {
      const parsed = JSON.stringify(this.books);
      localStorage.setItem(STORAGE_KEY, parsed);
    }
  }
};
</script>
