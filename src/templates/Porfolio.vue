<template>
    <Layout page="porfolio">
         <article class="porfolio">
            <figure class="porfolio__hero">
                <g-image :src="$page.post.hero_image" :alt="$page.post.title"></g-image>
            </figure>
            <div class="porfolio__info" >
            <h1>{{ $page.post.title }}</h1>
            <h3>{{ $page.post.date }}</h3>
            </div>
            <div class="porfolio__body" v-html="$page.post.content"></div>
            <div class="porfolio__footer">
                <h2>Written By: {{ $page.post.author }}</h2>
                <g-link :to="nextPorfolioPath">
                    <svg xmlns="http://www.w3.org/2000/svg"  version="1.1" x="0px" y="0px" viewBox="0 0 26 26" enableBackground="new 0 0 26 26" >
                        <path d="M23.021,12.294l-8.714-8.715l-1.414,1.414l7.007,7.008H2.687v2h17.213l-7.007,7.006l1.414,1.414l8.714-8.713  C23.411,13.317,23.411,12.685,23.021,12.294z"/>
                    </svg>
                </g-link>
            </div>
        </article>
    </Layout>
</template>

<script>
    export default {
        metaInfo() {
            return {
                title: this.$page.post.title
            }
        }, 
        computed: {
            nextPorfolioPath: function() {
                const allPorfolios = this.$page.all.edges
                const firstPorfolioPath = allPorfolios[0].node.path
                const currentPorfolio = allPorfolios.filter(node => node.node.title === this.$page.post.title)
                function isNull(item) {
                    return item == null || item == undefined
                }
                return isNull(currentPorfolio[0].next) ? firstPorfolioPath : currentPorfolio[0].next.path
            }
        } 
    }
</script>

<page-query>
query getPostData ($path: String!) {
    post: porfolio(path: $path) {
        title
        author
        content
        hero_image (quality: 80)
    }
    all: allPorfolio {
        edges {
            node {
                path
                title
            }
            next {
                path
            }
        }
    }
}

</page-query>

<style lang="scss" >
    .porfolio {
        h1 {
            margin-bottom: 0.7rem;
        }
    }

    .porfolio__hero {
        overflow: hidden;
        min-height: 300px;
        height: 60vh;
        width: 100%;
        margin: 0;
        img {
            min-width: 100%;
            min-height: 100%;
            margin-bottom: 0;
            object-fit: cover;
        }
    }

    .porfolio__info {
        text-align: center;
        padding: 1.5rem 1.25rem;
        width: 100%;
        max-width: 768px;
        margin: 0 auto;
        h1 {
            margin-bottom: 0.66rem;
        }
        h3 {
            margin-bottom: 0;
        }
    }

    .porfolio__body {
        width: 100%;
        padding: 0 1.25rem;
        margin: 0 auto;
        display: flex;
        flex-direction: column;
        justify-content: center;
        a {
            padding-bottom: 1.45rem;
        }
        :last-child {
            margin-bottom: 0;
        }
        h1, h2, h3, h4, h5, h6 {
            font-weight: normal;
            padding: 1.5rem;
            line-height: 1.2;
            margin-bottom: 1.5rem;
        }
        p {
            color: #111111;
            font-weight: normal;
            img {
                margin: 1rem 0;
            }
        }
        ul {
            list-style: initial;
        }
        ul, ol {
            margin-left: 1.25rem;
            margin-bottom: 1.25rem;
            padding-left: 1.45rem;
        }
    }

    .porfolio__footer {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1.5rem 1.25rem;
        width: 100%;
        max-width: 1280px;
        margin: 0 auto;
        h2 {
            margin-bottom: 0;
        }
        a {
            display: flex;
            justify-content: space-between;
            align-items: center;
            svg {
            width: 20px;
            }
        }
    }

    @media (min-width: 768px) {
        .porfolio {
            display: flex;
            flex-direction: column;
        }
        .porfolio__body {
            max-width: 1280px;
            padding: 0 2rem;
            span {
            width: 100%;
            margin: 1.5rem auto;
            }
            ul, ol {
            margin-left: 1.5rem;
            margin-bottom: 1.5rem;
            }
        }
        .porfolio__hero {
            min-height: 600px;
            height: 75vh;
            img {
            min-width: 100%;
            }
        }
        .porfolio__info {
            text-align: center;
            padding: 2rem 0;
            h1 {
            max-width: 500px;
            margin: 0 auto 0.66rem auto;
            }
        }
        .porfolio__footer {
            padding: 2.25rem;
        }
    }

    @media (min-width: 1440px) {
        .porfolio__hero {
            height: 70vh;
        }
        .porfolio__info {
            padding: 3rem 0;
        }
        .porfolio__footer {
            padding: 2rem 2rem 3rem 2rem;
        }
    }

</style>
