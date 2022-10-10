<template>
  <div>
    <input type="text" v-model="text" />
    <button @click="saveText">Save</button>
    <ul>
      <li v-for="(item, index) in data" :key="index">
        {{ item }} <button @click="editItem(index)">Edit</button>
        <button @click="deletItem(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      text: "",
      data: [],
      edit: null,
    };
  },
  methods: {
    saveText() {
      if (this.edit === null) {
        this.data.push(this.text);
        this.text = "";
      } else {
        this.data[this.edit] = this.text;
        (this.edit = null), (this.text = "");
      }
    },
    deletItem(index) {
      this.data.splice(index, 1);
    },
    editItem(index) {
      this.inp = this.data[index];
      this.edit = this.inp;
      this.data.filter((ele) => {
        if (this.data.indexOf(ele) === index) {
          this.inp = ele;
        }
      });
      this.edit = index;
    },
  },
};
</script>
<style scoped></style>
