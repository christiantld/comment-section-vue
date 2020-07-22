<template>
  <div class="form-todo form-group">
    <p>
      <input type="text" placeholder="nome" v-model="name" name="author" class="form-control" />
    </p>
    <p>
      <textarea
        name="message"
        id="message"
        cols="15"
        rows="5"
        placeholder="Comentário"
        v-model="message"
        class="form-control"
      ></textarea>
    </p>
    <button class="btn btn-primary" v-on:click="addComment">Comentar</button>
    <hr />
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      message: "",
    };
  },
  methods: {
    addComment() {
      if (!this.message.trim()) return;

      this.$emit("add-comment", {
        name: this.name,
        message: this.message,
      });

      this.name = "";
      this.message = "";
    },
  },
};
</script>