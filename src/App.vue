<template>
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

<style scoped></style>
