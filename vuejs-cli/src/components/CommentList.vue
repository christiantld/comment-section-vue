<template>
  <div class="container">
    <h1>Comentários</h1>
    <hr />
    <CommentForm v-on:add-comment="add" />
    <div class="list-group">
      <p v-if="comments.length <= 0" class="text-center text-muted">Sem comentários</p>
      <div class="list-group-item" v-for="(comment,index) in allComments" v-bind:key="index">
        <span class="comment__author">
          Autor:
          <strong>{{comment.name}}</strong>
        </span>
        <p>{{comment.message}}</p>
        <div>
          <a href="#" v-on:click.prevent="removeComment(index)" title="Excluir">Excluir</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CommentForm from "./CommentForm";
export default {
  components: {
    CommentForm,
  },
  data() {
    return {
      comments: [],
    };
  },
  methods: {
    add(comment) {
      this.comments.push(comment);
    },
    removeComment(index) {
      this.comments.splice(index, 1);
    },
  },
  computed: {
    allComments() {
      return this.comments.map((comment) => ({
        ...comment,
        name: !comment.name.trim() ? "Anónimo" : comment.name,
      }));
    },
  },
  watch: {
    comments(val) {
      console.log(("val", val));
    },
  },
};
</script>