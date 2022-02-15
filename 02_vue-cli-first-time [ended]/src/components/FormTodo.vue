<template>
  <div class="form-todo form-group">
    <p>
      <input
        type="text"
        class="form-control"
        v-model="name"
        placeholder="type your name here!"
        name="author"
      />
    </p>
    <p>
      <textarea
        name="message"
        placeholder="Comment"
        v-model="msg"
        class="form-control"
      ></textarea>
    </p>
    <button type="submit" v-on:click="addComment" class="btn btn-primary">
      Add Comment
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      msg: "",
    };
  },
  methods: {
    addComment() {
      if (this.msg.trim() === ``) {
        return;
      }

      this.$emit("add-todo", {
        name: this.name,
        msg: this.msg,
      });

      this.name = "";
      this.msg = "";
    },
  },
};
</script>