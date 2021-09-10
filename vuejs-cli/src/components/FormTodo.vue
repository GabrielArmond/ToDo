<template>
  <div class="form-todo from-group">
      <p>
        <input
          type="text"
          placeholder="Nome*"
          name="author"
          class="form-control"
          v-model="name"
          />
      </p>
      <p>
        <textarea
            name="message"
            placeholder="Comentário*"
            class="form-control"
            v-model="message"
        ></textarea>
      </p>
        <button v-on:click.prevent="addComment" type="submit" class="btn btn-primary" data-bs-toggle="button" autocomplete="off">Comentar</button>
        </div>
</template>

<script>
  export default{
    data() {
      return {
        name: '',
        message: ''
      }
    },
    methods: {
      addComment() {
        if (this.message.trim() === '') {
          return alert('Erro: campo comentário não preenchido')
        } 

        this.$emit('add-todo', {
          name: this.name,
          message: this.message
        })

        this.name = ''
        this.message = ''
      },
    },
  }
</script>