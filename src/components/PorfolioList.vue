<template>
    <section>
        <ul class="list">
             <g-link  v-for="post in posts" :key="post.node.title" :to="post.node.path" >
                <li>
                    <div class="hero_image">
                        <g-image 
                          :src="post.node.hero_image" 
                          :alt="post.node.title" 
                          width="300" 
                          height="300" 
                          quality="75">
                        </g-image>
                    </div>
                    <div class="blogList__info">
                        <h2>{{ post.node.title }}</h2>                       
                    </div>
                </li>
            </g-link>            
        </ul>
    </section>                       
</template>

<script>
    export default {
        props: {
            posts: {
                type: Array,
                required: true
            }
        },
        methods: {
          formatDate(date) {
            return new Date(date).toDateString().slice(4)
          }, 
          formatExcerpt(excerpt) {
            const blurb = excerpt.slice(3,200).trim()
            return blurb.indexOf('</p>') !== -1 ? blurb.slice( 0, blurb.indexOf('</p>')  ).trim()  + "..." : blurb  + "..."
          }
        }
    }
</script>

<style scoped lang="scss">
.list {
  div.hero_image {
          img {
            -webkit-transform: scale(1);
	          transform: scale(1);
            -webkit-transition: all 1s ease-in-out;
            transition: all .3s ease-in-out;
          }
}
    a:hover {
      opacity: 1;
      li {
        div.hero_image {
          img {
            -webkit-transform: scale(1.25);
	          transform: scale(1.25);
            -webkit-transition: all 1s ease;
            transition: all .3s ease;
          }
        }
      }
    }
    .hero_image {
      width: 100%;
      height: 45vh;
      overflow: hidden;
      background-color: #000;
      img {
        object-fit: cover;
        object-position: 50% 50%;
        opacity: 1;
        transition: opacity 0.3s ease;
        min-height: 100%;
      }
    }
    .blogList__info {
      display: flex;
      flex-direction: column;
      justify-content: center;
      padding: 0rem 1.5rem;
      border-bottom: 0px solid #bbbbbb;
      h2,
      h3,
      p {
        -webkit-transform: translateX(0px);
        transform: translateX(0px);
        -webkit-transition: transform 0.5 ease-out;
        transition: transform 0.5s ease-out;
      }
    }
  
    li {
      opacity: inherit;
      display: flex;
      justify-content: center;
      flex-direction: column;
      min-height: 38vh;
      margin-bottom: 0;
    }
    h2 {
      color: #5f5f5f;
      margin-bottom: 0rem;
      margin-top: -5rem;
      font-weight: normal;
      font-size: 25px;
      mix-blend-mode: multiply;
    }
    a:hover,
    a:hover h2 {
    color: #5F5F5F;
    transition: all 0.2s ease 0s;
    mix-blend-mode: color-dodge;
    }
  }
  
  @media (min-width: 768px) {
    .list {
      a:hover {
        
        opacity: 1;
        li {
          div.hero_image {
            cursor: url("https://img.icons8.com/ios/72/circled-chevron-right.png"), auto;
          }
          div.blogList__info {
            cursor: url("https://img.icons8.com/ios/72/circled-chevron-right.png"), auto;
          }
        }
      }
      li {
        min-height: 250px;
        height: 33.33vh;
        flex-direction: column;
      }
      
      .hero_image {
        height: 100%;
        min-width: 55%;
        img {
          
          min-width: 100%;
          height: 100%;
          width: auto;
          min-height: 0;
        }
      }
      .blogList__info {
        min-width: 45%;
      }
    }
  }
  
  @media (min-width: 1280px) {
    .list {
      .blogList__info {
        padding: 0rem 2rem 0rem;
      }
    }
  }
</style>
