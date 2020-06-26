<template>
  <Layout page="home">
  <div class="zoom">
  <g-image src="~/assets/content/images/call-waiting.png" width="750"/>
  </div>
  <h1 style="text-align:center">Hola, soy Nacho y esta es mi página principal.</h1>
  </Layout>
</template>


<script>
export default {
  metaInfo: {
    title: 'Home'
  }
}
</script>

<style lang="scss" scoped>
    .zoom {
      transition: transform .2s; /* Animation */
      margin: 0 auto;
      display: flex;
        justify-content: center;
        align-items: center;
    }

    .zoom:hover {
      transform: scale(1.05); /* (110% zoom - Note: if the zoom is too large, it will go outside of the viewport) */
    }
    .home {
        display: flex;
        justify-content: center;
        align-items: center;
    }
    h1 { 
	      position: relative; 
	      top: -150px;
}
</style>