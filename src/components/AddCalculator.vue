<!--  <template>
  <v-card class="overflow-hidden">
    <v-app-bar
      absolute
      color="#6A76AB"
      dark
      shrink-on-scroll
      prominent
      src="https://picsum.photos/1920/1080?random"
      fade-img-on-scroll
      scroll-target="#scrolling-techniques-3"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(100,115,201,.7), rgba(25,32,72,.7)"
        ></v-img>
      </template>

      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-app-bar-title>Title</v-app-bar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>

      <template v-slot:extension>
        <v-tabs align-with-title>
          <v-tab>Tab 1</v-tab>
          <v-tab>Tab 2</v-tab>
          <v-tab>Tab 3</v-tab>
        </v-tabs>
      </template>
      
    </v-app-bar>

    <v-sheet
      id="scrolling-techniques-3"
      class="overflow-y-auto"
      max-height="600"
    >
    
      <v-container style="height: 1000px"> </v-container>
    </v-sheet>
    <div>
      <v-text-field v-model="inp" label="Add"></v-text-field>
      <v-btn class="mx-2" fab dark color="indigo" @click="add">
        <v-icon dark> mdi-plus </v-icon>
      </v-btn>
      <v-list>
        <v-list-item v-for="(item, index) in data" :key="index">
          <v-list-item-icon>
            <v-icon v-if="item.icon" color="pink"> mdi-star </v-icon>
          </v-list-item-icon>
          <v-btn class="pa-2" fab dark color="indigo" @click="editItem(index)">
            <v-icon small> mdi-pencil </v-icon>
          </v-btn>
          <v-btn
            class="pa-2"
            fab
            dark
            color="indigo"
            @click="removeItem(index)"
          >
            <v-icon small> mdi-delete </v-icon>
          </v-btn>
          <v-list-item-content>
            <v-list-item-title v-text="item"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </div>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      inp: "",
      data: ["item one", "item two", "item three"],
      edit: null,
    };
  },
  methods: {
    add() {
      if (this.edit === null) {
        this.data.push(this.inp);
        this.inp = "";
      } else {
        this.data[this.edit] = this.inp;
        this.edit = null;
        this.inp = "";
      }
    },
    removeItem(ind) {
      this.data.splice(ind, 1);
    },
    editItem(ind) {
      this.inp = this.data[ind];
      this.edit = this.inp;
      this.data.filter((ele) => {
        if (this.data.indexOf(ele) === ind) {
          this.inp = ele;
        }
      });
      this.edit = ind;
    },
  },
};
</script>

<style scoped></style> -->

<!-- <template>
  <div>
    <h1>The First Add</h1>
    <button v-on:click="add(10)">Add 10</button><br />
    <button v-on:click="reduce(5)">Substract 5</button> <br />
    <p v-once>Starting Value: {{ counter }}</p>
    <p>Result: {{ counter }}</p> -->

<!-- <input type="text" v-on:input="setName" v-on:keyup.enter="confirmedInput" />
    <p>Your Name:{{ confirmeName }}</p> -->
<!-- <input type="text" v-model="name" />
    <button v-on:click="resetValue">Reset</button>
    <p>Your Name: {{ name }}</p>

    <form v-on:submit.prevent="submitted">
      <input type="text" />
      <button>Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      counter: 10,
      name: "",
      confirmeName: "",
    };
  },
  methods: {
    resetValue() {
      this.name = "";
    },
    confirmedInput() {
      this.confirmeName = this.name;
    },
    submitted() {
      alert("Submitted!");
    },
    setName(event) {
      this.name = event.target.value;

      //here event value is set by browser
    },
    add(num) {
      this.counter += num;
    },
    reduce(num) {
      this.counter -= num;
    },
  },
};
</script>

<style scoped></style> -->

<template>
  <div>
    <h1>The Content Of Add</h1>
    <h1>The Input Value</h1>
    <button @click="add(10)">ADD 10</button>
    <button @click="reduce(5)">SUBSTRACT 5</button>
    <p v-once>STARTING VALUE: {{ counter }}</p>
    <p>RESULT: {{ counter }}</p>

    <input type="text" v-model="name" />
    <button @click="resetValue()">RESET</button>
    <p>Your Name: {{ fullName }}</p>
  </div>
</template>
<script>
export default {
  data() {
    return {
      counter: 10,
      name: "",
    };
  },
  computed: {
    fullName() {
      if (this.name === "") {
        return "";
      } else {
        return this.name;
      }
    },
  },

  methods: {
    add(num) {
      this.counter += num;
    },
    reduce(num) {
      this.counter -= num;
      if (this.counter <= 0) {
        return (this.counter = 0);
      }
    },
    resetValue() {
      this.name = "";
    },
  },
};
</script>

<style scoped>
div {
  text-align: center;
  border: 2px solid rebeccapurple;
  max-width: 30%;
  margin-inline: auto;
  padding: 1rem;
  border-radius: 3rem;
}
button {
  margin-top: 2rem;
  margin-inline: 4rem auto;
  border: 2px dashed black;
  padding: 0.5rem;
  background-color: firebrick;
  font-weight: bold;
  color: whitesmoke;
  border-radius: 2rem;
}
h1,
h2 {
  color: blueviolet;
}
p {
  background-color: aqua;
  border: 2px solid gray;
  margin-top: 1rem;
  text-align: left;
  padding: 1rem;
  border-radius: 3rem;
  font-weight: bolder;
}
input {
  margin-top: 1rem;
  font-size: 1.5rem;
  padding: 10px;
  border: 2px solid gold;
  border-radius: 2rem;
}
</style>
