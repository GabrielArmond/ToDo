<template>
  <div class="container">
    <h1>Comentários</h1>
    <hr />
    <FormTodo v-on:add-todo="addComment" ></FormTodo>
        <hr />
      <div class="list-group">
        <p v-if="comments.length <= 0">Sem comentários...</p> 
      <div class="list-group-item" v-for="(comment, index) in allComments" v-bind:key="comment.id">
          <span class="comment__author">Autor: <strong>{{ comment.name }}</strong></span>
          <p>{{ comment.message }}</p>
          <div>
            <button @click.prevent="removeComment(index)" class="btn btn-danger btn-sm" type="submit">Excluir</button>
          </div>
        </div>
    </div>
  </div>
</template>

<script>

import FormTodo from "./FormTodo.vue"

export default {
  components: {
    FormTodo
  },
  data() {
    return {
      comments: [],
    }
  },
  methods: {
    addComment(comment) {
      this.comments.push(comment);
    },

    removeComment(index) {
      this.comments.splice(index, 1)
    }
  },
  computed: {
    allComments() {
      return this.comments.map(comment => ({
        ...comment,
        name: comment.name.trim() === '' ? 'Anônimo' : comment.name
      }))
    }
  },
  watch: {
    comments(values) {
      console.log('values', values)
    }
  }
}
</script>

