<template>
  <div class="navbar">
    <div class="logo">
      <img src="./assets/logo.png" style="width: 80px" />
    </div>

    <div class="nav_button_container">
      <div class="btn" @click="$emit('show1')">Table</div>
      <div class="btn" @click="$emit('show2')">Flex</div>
      <div class="btn" @click="$emit('showlist')">Sort</div>

      <div class="btn" @click="$emit('show1')">xxxxx</div>
      <div class="btn" @click="$emit('show2')">yyyyyyyy</div>
      <div class="btn" @click="mymeth('ZZZ')">zz</div>

      <div class="btn" @click="$emit('show1')">111</div>
      <div class="btn" @click="$emit('show2')">2222</div>
      <div class="btn" @click="$emit('showlist')">3333</div>
    </div>
  </div>
  <div class="content">
    <button @click="mypopup">Open Popup...</button>
    <!-- embed  type="text/plain" src="./assets/text.txt" /      geht nicht -->
    <p>Filter val in App.vue: {{ myFilVal }}</p>
    <Table
      :myfields="myfields"
      :studentData="studentDatax"
      :myFilter="myFilVal"
    ></Table>

    <div ref="myModal" class="modal">
      <div class="modal-content">
        <span class="close" @click="mypopup">&times;</span>
        <p>Enter number to filter age for</p>
        <myInput @setfilterto="setfilter" />
      </div>
    </div>
  </div>
</template>

<script>
import Table from "./components/table.vue";
import myInput from "./components/input.vue";
import mydata from "./assets/data.json";
import "./App.css";

export default {
  name: "App",
  components: {
    Table,
    myInput,
  },
  methods: {
    mymeth() {
      alert("xxx mymeth() called.");
    },
    setfilter(fil_) {
      console.log("filterxxx" + fil_);
      this.myFilVal = Number(fil_);
      this.mypopup();
    },
    mypopup() {
      //this.$refs.myModal.style="display:block";
      if (this.$refs.myModal.style.display === "block")
        this.$refs.myModal.style = "display:none";
      else this.$refs.myModal.style = "display:block";
      //console.log(this.$refs.myModal.style);
    },
  },
  mounted() {
    console.log(Date.now() + "Mounted. Starting...");
  },

  data() {
    return {
      myFilVal: "23",
      myfields: mydata.myfields,

      studentDatax: mydata.studs,
    };
  },
};
</script>

<style>
</style>