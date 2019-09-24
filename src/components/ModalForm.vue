<template>
  <form v-on:submit.prevent>
    <div class="modal-card" style="max-width: 700px">
      <header class="modal-card-head">
        <p class="modal-card-title">Form</p>
      </header>
      <section class="modal-card-body">
        <b-field label="Name">
          <b-input placeholder="Your Name" v-model.lazy="author" required></b-input>
        </b-field>

        <b-field label="Content">
          <b-input maxlength="200" type="textarea" v-model.lazy="content" placeholder="add your content" required></b-input>
        </b-field>

      </section>
      <footer class="modal-card-foot">
        <button class="button" type="button" @click="$parent.close()">Close</button>
        <button class="button is-primary" @click="onClick()">Submit</button>
      </footer>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      author: '',
      content: '',
    }
  },
  methods: {
    onClick(event){
      this.$emit('submitted', { author: this.author, content: this.content});
    }
  }
}
</script>