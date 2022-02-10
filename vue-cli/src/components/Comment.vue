<template>
  <div class="container">
    <h1>Comments</h1>
    <hr />

    <FormTodo v-on:add-todo="makeComment"> </FormTodo>

    <div class="list-group">
      <p v-if="comments.lenght <= 0">Sem comentarios.....</p>
      <div
        class="list-group-item"
        v-for="(c, index) in allComments"
        v-bind:key="index"
      >
        <span class="comment__author">
          Author: <b>{{ c.name }}</b>
        </span>
        <p>{{ c.msg }}</p>
        <div>
          <a href="#" title="del" v-on:click.prevent="delComment(index)">
            Delete
          </a>
        </div>
      </div>
    </div>
    <hr />
  </div>
</template>

<script>
import FormTodo from "./FormTodo";
export default {
  components: {
    FormTodo,
  },
  data() {
    return {
      comments: [],
      name: "",
      msg: "",
    };
  },
  methods: {
    delComment(index) {
      this.comments.splice(index, 1);
    },
    makeComment(data) {
      this.comments.push(data);
    },
  },
  computed: {
    allComments() {
      return this.comments.map((c) => ({
        ...c,
        name: c.name.trim() === `` ? `Anonymous` : c.name,
      }));
    },
  },
  watch: {
    comments(value) {
      console.log("value :>> ", value);
    },
  },
};
</script>