<template>
    <header class="header">
        <nav class="nav">
            <g-link to="/" exact>
                <g-image class="logo" src="~/assets/content/images/logo.svg" width="150"/>
            </g-link>
            <div class="notranslate"></div>
            <div class="links">
                    <g-link to="/porfolio/">
                    work
                    </g-link>
    
                    <g-link to="/blog/">
                    blog
                    </g-link>
                
                    <g-link :to="infoLink">
                        {{ isInfoPage ? "X&nbsp;" : "info" }}
                    </g-link>                    
            </div>
        </nav>
    </header>
</template>

<script>
export default {
    props: {
        page: {
            type: String,
            required: true
        }
    },
    computed: {
        isInfoPage() {
            return this.page === "info" && true
        },
        infoLink() {
            return this.isInfoPage ? "/" : "/info"
        }, 
    }
}
</script>

<static-query>
    query {
    metadata {
        siteName
    }
    }
</static-query>

<style>
.header h1 {
    margin-bottom: 0; 
}
  
.nav {
    padding: 1.5rem 1.25rem;
    border-bottom: 0px solid #bbbbbb;
    display: flex;
    justify-content: space-between;
    flex-direction: row;
    align-items: center;
}

.nav img {
     margin-bottom: 0;
}

.links {
    display: flex;
    flex-direction: column;
    gap: 10px;
    flex-wrap: no-wrap;
}


@media only screen and (max-width: 640px) { 
    .header {
       font-size: 1.25rem;
    }
    
    br {
        display: none;
    }
    .links {
    flex-direction: row;
    gap: 1.25rem;
    }

    .logo {
        max-width: 6rem;
    }

}



@media (min-width: 768px) {
    .header {
      flex-wrap: wrap;
      font-size: 2rem;
      height: 100vh;
      position: fixed;
      left: 0;
      top: 0;
    }
    
    .nav {
      padding: 2rem;
      width: 20vw;
      height: 100%;
      border-right: 1px solid #bbbbbb;
      border-bottom: none;
      flex-direction: column;
      align-items: flex-start;
    }
    
}


</style>
