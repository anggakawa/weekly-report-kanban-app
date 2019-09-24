<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title">
        {{ author }}
      </p>
      <a href="#" class="card-header-icon" aria-label="more options">
        <span class="icon">
          <i class="fas fa-angle-down" aria-hidden="true"></i>
        </span>
      </a>
    </header>
    <div class="card-content">
      <div class="content">
        {{ content }}
      </div>
    </div>
    <footer class="card-footer">
      <a class="card-footer-item" @click="deleteObject">Delete</a>
    </footer>
  </div>
</template>

<script>
export default {
  name : 'card-component',
  props : [
    'author',
    'content',
  ],
  methods: {
    deleteObject() {
      this.$emit('deleted');
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .content {
    text-align: left;
  }
</style>