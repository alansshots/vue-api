<template>
  <div>
      <hr>
      <button>DELETE</button>
      <h2>{{userId}}</h2>
      <h2>{{title}}</h2>
      <p>{{body}}</p>
  </div>
</template>

<script>
export default {
    name:'Post',
    props: {
        userId: String,
        title: String,
        body: String
    },
    data(){
        return {

        }
    }
}
</script>

<style>

</style>