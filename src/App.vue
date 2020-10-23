<template>
  <div>
    <div class="t1 p-9">
      <h3 class="p-3 text-center">Obtiene la poblacion total por codigo postal</h3>
    </div>
    <get-request />
  </div>
</template>

<script>
import GetRequest from "./components/GetRequest";

export default {
  name: "app",
  components: {
    GetRequest
  }
};
</script>

<style>
.t1 {
  color: silver;
  background-color: black;
}
.t2 {
  color: grey;
  background-color: black;
}
</style>
