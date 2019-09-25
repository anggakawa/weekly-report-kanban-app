<template>
  <div class="section">
    <div class="container">
      <div class="level">
        <div class="level-left">
          <div class="level-item">
            <b-field label="Name" label-position="inside">
              <b-input v-model="name" required></b-input>
            </b-field>
          </div>
          <div class="level-item">
          <b-field label="Week" label-position="inside">
              <b-select placeholder="Select Weekly Report">
                <option value="1">Option 1</option>
                <option value="2">Option 2</option>
              </b-select>
            </b-field>
          </div> 
        </div>
        <div class="level-right">
          <div class="level-item">
            <b-button type="is-info" outlined>Minggu ke - {{ week }}</b-button>
          </div>
          <div class="level-item">
            <b-button @click="newWeek">Add</b-button>
          </div>
          <div class="level-">
            <b-button type="is-success">Save</b-button>
          </div>
        </div>
      </div>
    </div>
    <div class="container">
      <div class="columns">
        <div class="column">
          <h3>Todo:</h3>
          <div class="cards" v-for="data in todo">
            <CardComponent
              :author="data.author"
              :content="data.content"
              @deleted="deleteObject(data, 'todo')"
            />
          </div>
          <div>
            <b-button @click="addData('todo')">Tambah</b-button>
          </div>
        </div>
        <div class="column">
          <h3>Ongoing:</h3>
          <div class="cards" v-for="data in ongoing">
            <CardComponent
              :author="data.author"
              :content="data.content"
              @deleted="deleteObject(data, 'ongoing')"
            />
          </div>
          <div>
            <b-button @click="addData('ongoing')">Tambah</b-button>
          </div>
        </div>
        <div class="column">
          <h3>Done:</h3>
          <div class="cards" v-for="data in done">
            <CardComponent
              :author="data.author"
              :content="data.content"
              @deleted="deleteObject(data, 'done')"
            />
          </div>
          <div>
            <b-button @click="addData('done')">Tambah</b-button>
          </div>
        </div>
      </div>
    </div>
    <div class="container">
      <b-modal :active.sync="isComponentModalActive" has-modal-card>
        <modal-form @submitted="getData"></modal-form>
      </b-modal>
    </div>
  </div>
</template>

<script>
import CardComponent from "./CardComponent";
import ModalForm from "./ModalForm";

export default {
  name: "HelloWorld",
  components: {
    CardComponent,
    ModalForm
  },
  data() {
    return {
      name: "",
      isComponentModalActive: false,
      dataType: "",
      week: 0,
      todo: [
        {
          author: "Corrine Kozey",
          content:
            "Illum eos facere dolores voluptatem officia minus occaecati. Autem non vero qui corrupti sint odit officiis officiis sunt. At voluptas dolorum rem accusantium corrupti. Atque est fuga voluptatem aliquid dolor harum quo libero maxime. Facere est culpa adipisci rerum iure sint odio. Vitae sed aut aut et rerum ratione perferendis explicabo."
        },
        {
          author: "Alford Schoen DDS",
          content:
            "Dignissimos at quia rerum porro vitae ea aliquid. Deserunt est facilis maiores. Iste sint debitis fugiat illum doloremque consequatur."
        },
        {
          author: "Johnpaul Mraz",
          content:
            "Eligendi enim voluptatum molestiae modi atque assumenda id quae. Recusandae libero autem ea eveniet qui rem. A id est."
        }
      ],
      ongoing: [
        {
          author: "Krista Rosenbaum",
          content:
            "Ea laudantium facilis numquam perspiciatis iure. Reiciendis omnis omnis qui nihil sit dolorum aut quaerat vitae. Amet facere explicabo quia."
        },
        {
          author: "Cristopher Hettinger",
          content:
            "Ea laudantium facilis numquam perspiciatis iure. Reiciendis omnis omnis qui nihil sit dolorum aut quaerat vitae. Amet facere explicabo quia."
        },
        {
          author: "Jaron Pagac",
          content:
            "Ea laudantium facilis numquam perspiciatis iure. Reiciendis omnis omnis qui nihil sit dolorum aut quaerat vitae. Amet facere explicabo quia."
        },
        {
          author: "Golda Daniel",
          content:
            "Doloribus eos eum facilis. Ratione eius aut. Qui dolorem libero. Deleniti numquam magni laboriosam debitis velit ut."
        },
        {
          author: "Ernie Wisozk",
          content:
            "Ea laudantium facilis numquam perspiciatis iure. Reiciendis omnis omnis qui nihil sit dolorum aut quaerat vitae. Amet facere explicabo quia."
        }
      ],
      done: [
        {
          author: "Uriel Nader",
          content:
            "Ea laudantium facilis numquam perspiciatis iure. Reiciendis omnis omnis qui nihil sit dolorum aut quaerat vitae. Amet facere explicabo quia."
        },
        {
          author: "Madisen Macejkovic",
          content:
            "Ea laudantium facilis numquam perspiciatis iure. Reiciendis omnis omnis qui nihil sit dolorum aut quaerat vitae. Amet facere explicabo quia."
        }
      ]
    };
  },
  methods: {
    addData(type) {
      this.dataType = type;
      this.isComponentModalActive = true;
    },
    getData(data) {
      if (this.dataType === "todo") {
        this.todo.push(data);
      } else if (this.dataType === "ongoing") {
        this.ongoing.push(data);
      } else if (this.dataType === "done") {
        this.done.push(data);
      }
      this.isComponentModalActive = false;
      this.dataType = "";
    },
    newWeek() {
      this.todo = [];
      this.ongoing = [];
      this.done = [];
      this.week++;
    },
    deleteObject(data, dataType) {
      console.log(data);
      if (dataType === "todo") {
        this.todo.splice(this.todo.findIndex(x => x.author === data.author), 1);
      } else if (dataType === "ongoing") {
        this.ongoing.splice(
          this.ongoing.findIndex(x => x.author === data.author),
          1
        );
      } else if (dataType === "done") {
        this.done.splice(this.done.findIndex(x => x.author === data.author), 1);
      }
    }
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
