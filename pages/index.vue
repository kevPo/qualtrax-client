<template>
  <div>
    <div class="label-input">
      <label>Site URL</label>
      <input type="text">
    </div>

    <div class="label-input">
      <label>User Id</label>
      <input type="text">
    </div>

    <div class="label-input">
      <label>User Agent</label>
      <input type="text">
    </div>

    <div class="label-input">
      <label>Token</label>
      <input type="text">
    </div>
  </div>
</template>

<script>

export default {

}
</script>

<style>
.label-input {
  display: grid;
  grid-template-columns: 200px auto;
  grid-gap: 10px;
  padding: 10px;
}

.label-input label {
  text-align: right;
}

.label-input input {
  padding: 5px;
}
</style>
