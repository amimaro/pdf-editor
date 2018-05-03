<template>
<div class="drop-file" @dragover.prevent @drop="onDrop">
  <div class="helper"></div>
  <label class="btn">
    Select or Drop a PDF
    <input type="file" @change="onChange">
  </label>
</div>
</template>

<script>
export default {
  name: 'landing-page',
  components: {},
  data() {
    return {}
  },
  methods: {
    onDrop: function(event) {
      event.stopPropagation()
      event.preventDefault()
      let files = event.dataTransfer.files
      this.loadFile(files[0])
    },
    onChange(event) {
      let files = event.target.files
      this.loadFile(files[0])
    },
    loadFile(file) {
      if (!file.type.match('application/pdf')) {
        alert('Select a PDF')
        return
      }
      let reader = new FileReader();
      reader.readAsArrayBuffer(file);
      reader.onload = function(e) {
        const uint8Array = new Uint8Array(reader.result)
        localStorage.setItem('pdf-editor', JSON.stringify(uint8Array))
      }
      this.$router.push('editor')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
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
