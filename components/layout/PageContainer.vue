<template>
  <!-- root -->
  <div class="page-container">
    <!-- header -->
    <div class="page-container-header">
      <slot name="header" />
    </div>
    <!-- contents -->
    <div class="page-container-contents">
      <slot />
    </div>
    <!-- footer -->
    <div class="page-container-footer">
      <slot name="footer" />
    </div>
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
  font-size:16px;
}

.page-container{
  width:100vw;height:100vh;
  display:flex;
  flex-direction: column;
  align-items: center;
  background:white;
}

.page-container-header{
  width:100%;height:40px;background:orange;opacity: 0.5;
}

.page-container-footer{
  width:100%;height:40px;background:blue;opacity: 0.5;
}

.page-container-contents{
  width:100%;
  height:calc(100% - 80px);
  overflow-y:auto;
  background:rgb(243, 243, 243);
}

@media screen and (min-width: 900px) {
  body{
    font-size:16px;
  }
  .page-container-contents{
    width:900px;
    overflow:auto;
  }
}

</style>
