<template>
  <div class="about">
    <h1>This is an about page {{ count }} {{ title }}</h1>
    <div v-if="show">
      <button v-on:click="count++">Click me</button>
      <div @click="changeTitle('Maintenant un autre titre')">Change title</div>
    </div>
    <div v-show="show">currently showing</div>
    <button @click="toggleShow">
      <span v-if="show">Hide Truc</span>
      <span v-else>Show Truc</span>
    </button>
    <br />
    <div class="box" @mouseover="handleEvent">mouseover (enter)</div>
    <div class="box" @mouseleave="handleEvent">mouseleave</div>
    <div class="box" @dblclick="handleEvent">double click</div>
    <div class="box" @mousemove="handleMousemove">
      position - {{ x }} - {{ y }}
    </div>
    <ul>
      <li v-for="book in books" :class="{ fav: book.isFav }">
        <img :src="book.img" :alt="book.title" />
        <h3>{{ book.title }}</h3>
        <p>{{ book.author }}</p>
        <a @click="addFav(book)">Add to fav</a>
      </li>
    </ul>
    <a :href="url">Go Home</a>

    <p>Fav Books</p>
    <ul>
      <li v-for="book in filteredBooks" :class="{ fav: book.isFav }">
        <h3>{{ book.title }}</h3>
      </li>
    </ul>
  </div>
</template>

<style>
li {
  list-style-type: none;
  margin: 20px auto;
  padding: 10px 20px;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

li.fav {
  background: rgb(126, 126, 0);
}

.box {
  padding: 100px 0;
  width: 400px;
  text-align: center;
  background: #ddd;
  margin: 20px;
  display: inline-block;
  color: black;
}
</style>

<script lang="ts">
export default {
  data() {
    return {
      show: true,
      title: "Je suis un titre",
      count: 0,
      x: 0,
      y: 0,
      books: [
        {
          title: "name 1",
          author: "author 1",
          img: "/src/assets/livre1.png",
          isFav: true,
        },
        {
          title: "name 2",
          author: "author 2",
          img: "/src/assets/livre2.png",
          isFav: false,
        },
        {
          title: "name 3",
          author: "author 3",
          img: "/src/assets/livre3.png",
          isFav: true,
        },
      ],
      url: "http://127.0.0.1:5173/",
    };
  },
  methods: {
    addFav(book: any) {
      book.isFav = !book.isFav;
    },
    changeTitle(newTitle: any) {
      this.title = newTitle;
    },
    toggleShow() {
      this.show = !this.show;
    },
    handleEvent(e: any) {
      console.log(e, e.type);
    },
    handleMousemove(e: any) {
      this.x = e.offsetX;
      this.y = e.offsetY;
    },
  },
  computed:{
    filteredBooks(){
      return this.books.filter((book) => book.isFav);
    }
  }
};
</script>
