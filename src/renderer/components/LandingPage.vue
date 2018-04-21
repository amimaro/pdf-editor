<template>
<div id="landing-page">
  <center>
    <div class="table">
      <div class="row">
        <div class="element-cell" style="padding-right: 15px">
          <h1>
          Drop your file in the box below or
        </h1>
        </div>
        <div class="cell">
          <input type="file">
        </div>
      </div>
    </div>
    <div id="drop-file">
    </div>
  </center>
</div>
</template>

<script>
export default {
  name: 'landing-page',
  components: {},
  methods: {},
  data() {
    return {}
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
}

#landing-page {

}

#drop-file {
  width: 150vh;
  height: 80vh;
  margin-top: 10px;
  border-style: dashed;
  border-color: gray;
  color: gray;
  vertical-align: middle;
}
</style>
