<template>
<div>
  <h1>Hello</h1>
  <button type="button" name="button" @click="home">return</button>
</div>
</template>

<script>
export default {
  name: 'editor-page',
  components: {},
  data() {
    return {
      path: ''
    }
  },
  created: function () {
    let obj = JSON.parse(localStorage.getItem('pdf-editor'))
    this.path = obj.path
  },
  methods: {
    home: function () {
      this.$router.push('/')
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Quicksand', sans-serif;
  padding: 10px;
  height: 100%;
  text-align: center;
}

.btn {
  background-color: #4c39d3;
  border: 0;
  color: #fff;
  cursor: pointer;
  display: inline-block;
  font-weight: bold;
  padding: 15px 35px;
  position: relative;
}

.btn:hover {
  background-color: #402072;
}

input[type="file"] {
  position: absolute;
  opacity: 0;
  z-index: -1;
}

.align-center {
  text-align: center;
}

.helper {
  height: 100%;
  display: inline-block;
  vertical-align: middle;
  width: 0;
}

.hidden {
  display: none !important;
}

.hidden.image {
  display: inline-block !important;
}

.display-inline {
  display: inline-block;
  vertical-align: middle;
}

.img {
  border: 1px solid #f6f6f6;
  display: inline-block;
  height: auto;
  max-height: 80%;
  max-width: 80%;
  width: auto;
}

.drop-file {
  margin-top: 20px;
  background-color: #f0f2ff;
  border: 10px dashed #aaa;
  border-radius: 10px;
  height: 80vh;
  width: 100vh;
  text-align: center;
  display: inline-block;
  vertical-align: middle;
}
</style>
