
<template>
    <Layout>
        <div class="not-found">
            <h2>
                <g-image src="~/assets/content/images/Astronaut-404.png" width="500"/>
            </h2>
    
            <h2>
                <g-link to="/">
                    Sorry, couldn't find that page...
                </g-link>
            </h2>
        </div>

    </Layout>
</template>

<script>
    export default {
        metaInfo() {
          return {
            title: "Not Found",
          }
      }
    }
</script>

<style lang="scss" scoped>
    .not-found {
        width: 100%;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }
</style>