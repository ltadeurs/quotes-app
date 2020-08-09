<template>
  <div>
    <h1 class="title">{{ msg }}</h1>
    <div class="container">
      <button v-on:click="getQuote">Get Quote of the day</button>
      <button v-on:click="getCategories">Get Quote categories</button>
      <div v-if="quote !=''" class="block grow">
        <p class="quote">{{ quote }}</p>
        <p class="author">- {{ author }} -</p>
      </div>
      <div v-if="visible" class="categoryList">
        <h3>Search Categories</h3>
        <input type="text" v-model="search" />
        <div v-for="(value, name) in categories" v-bind:key="value">
          <div id="category" v-if="!search || name.startsWith(search)">
            <p class="cName">{{ name }}:</p>
            <p class="cDescr">{{ value }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "QuoteApi",
  props: {
    msg: String,
  },
  data() {
    return {
      visible: false,
      search: "",
      quote: "",
      author: "",
      categories: [],
    };
  },
  methods: {
    getQuote() {
      fetch("https://quotes.rest/qod?language=en")
        .then((response) => response.json())
        .then((data) => {
          this.quote = '"' + data.contents.quotes[0].quote + '"';
          this.author = '"' + data.contents.quotes[0].author + '"';
          
          // UI changes
          this.visible = false;
          this.categories = [];
        });
    },
    getCategories() {
      fetch("https://quotes.rest/qod/categories?language=en&detailed=false")
        .then((response) => response.json())
        .then((data) => {
          this.categories = data.contents.categories;

          // UI changes
          this.visible = true;
          this.quote = "";
          this.author = "";
        });
    },
  },
};
</script>