<template>
  <Layout page="blog">
    <BlogList :posts="$page.posts.edges" />
  </Layout>
</template>

<script>
import BlogList from '~/components/BlogList.vue'

export default {
  metaInfo: {
    title: 'Blog'
  },
  components: {
    BlogList
  }
}
</script>

<page-query>
    query getAllBlogData {
        posts: allBlog {
            edges {
                node {
                    id
                    title
                    path
                    author
                    date  (format: "MMMM DD YYYY")
                    hero_image (width:1000, quality: 75)
                    content
                }
            }
        }
    }
</page-query>
