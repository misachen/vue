<template>
  <div class="hello">
    <div class="form-group has-success">
      <label class="form-control-label" for="inputSuccess1">Input with success</label>
      <input type="text" class="form-control form-control-success" id="inputSuccess1">
      <div class="form-control-feedback">Success! You've done it.</div>
      <small class="form-text text-muted">Example help text that remains unchanged.</small>
    </div>
    <div class="form-group has-warning">
      <label class="form-control-label" for="inputWarning1">Input with warning</label>
      <input type="text" class="form-control form-control-warning" id="inputWarning1">
      <div class="form-control-feedback">Shucks, check the formatting of that and try again.</div>
      <small class="form-text text-muted">Example help text that remains unchanged.</small>
    </div>
    <div class="form-group has-danger">
      <label class="form-control-label" for="inputDanger1">Input with danger</label>
      <input type="text" class="form-control form-control-danger" id="inputDanger1">
      <div class="form-control-feedback">Sorry, that username's taken. Try another?</div>
      <small class="form-text text-muted">Example help text that remains unchanged.</small>
    </div>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
