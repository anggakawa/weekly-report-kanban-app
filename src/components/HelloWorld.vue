<template>
  <div class="section">
    <div class="container">
      <div class="level">
        <div class="level-left">
          <b-field horizontal label="Week">
            <b-select placeholder="Select Weekly Report">
              <option value="1">Option 1</option>
              <option value="2">Option 2</option>
            </b-select>
          </b-field>
        </div>
      </div>
    </div>
    <div class="container">
      <div class="columns">
        <div class="column">
          <h3>Todo:</h3>
          <div class="cards" v-for="n in 5">
            <CardComponent />
          </div>
          <div>
            <b-button>Tambah</b-button>
          </div>
        </div>
        <div class="column">
          <h3>Ongoing:</h3>
          <div class="cards" v-for="n in 3">
            <CardComponent />
          </div>
          <div>
            <b-button>Tambah</b-button>
          </div>
        </div>
        <div class="column">
          <h3>Done:</h3>
          <div class="cards" v-for="n in 2">
            <CardComponent />
          </div>
          <div>
            <b-button>Tambah</b-button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CardComponent from "./CardComponent";

export default {
  name: "HelloWorld",
  components: {
    CardComponent
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  margin-bottom: 1.25em;
}
.column {
  border: 1px solid black;
  margin: 1em;
}
.cards {
  padding: 0.75em;
}
</style>
