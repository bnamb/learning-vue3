<template>
    <section @click="$emit('close-login')" class="z-20 h-screen w-screen bg-gray-300 opacity-50 fixed top-0"></section>
  <div class="absolute inset-0">
    <div class="flex h-full">
      <div class="z-30 m-auto bg-white p-2 shadow rounded">
        <h1>Login</h1>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  
}
</script>

<style>

</style>