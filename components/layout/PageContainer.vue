<template>
  <div class="page-container">
    <slot />
  </div>
</template>

<script>
export default {
  name: 'PageContainer'
}
</script>

<style>
*{
  box-sizing: border-box;
}
body{
  margin:0px;
}

.page-container{
    width:calc(100vw - 20px);height:calc(100vh - 20px);
    border:1px solid red;
    margin:10px;
    padding:20px;
}
</style>
