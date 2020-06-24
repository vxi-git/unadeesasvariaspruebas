<template>
  <Layout page="home">
    <PorfolioList :posts="$page.posts.edges" />
  </Layout>
</template>

<script>
import PorfolioList from '~/components/PorfolioList.vue'

export default {
  metaInfo: {
    title: 'Porfolio'
  },
  components: {
    PorfolioList
  }
}
</script>

<page-query>
    query getAllPorfolioData {
        posts: allPorfolio {
            edges {
                node {
                    id
                    title
                    path
                    author
                    hero_image (width:1000, quality: 75)
                    content
                }
            }
        }
    }
</page-query>
