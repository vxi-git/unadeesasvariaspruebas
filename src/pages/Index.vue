<template>
  <Layout page="home">
    <div class="container">
      <a class="circle"></a>
      <h1>Hola, soy Nacho y esta es mi página principal.</h1>
      <button class="custom-btn btn-16"><a href="http://localhost:8080/porfolio/">Selected Work</a></button>
    </div>

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
    .container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }

    h1 {
    margin-top: 15rem;
  }

  @media (max-width: 800px) {
  .container {
    position: relative; top:-8rem; left:1rem;

  a.circle {
    width:60vmin;
    height:60vmin;
    }
  } 
}


/*sticker*/
a.circle {
  width: 30vmin;
  height: 30vmin;
  transform-style: preserve;
  position: relative; left:5rem; top:10rem;  
  
  &:before, &:after {
    content:'';
    display: block;
    position: absolute;
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background:center/cover url(https://images.unsplash.com/photo-1549887534-1541e9326642?ixlib=rb-1.2.1&ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&auto=format&fit=crop&w=701&q=80);  
  }
  
  &:before {
    animation: f 4s both;
    @keyframes f {
      from {clip-path:inset(0 80% 0 0);}
      50%, to {clip-path:inset(0 0% 0 0);}
    }  
  }
  
  &:after {
    filter: brightness(0.2);
    transform: rotateY(-180deg);
    animation: g 4s both;
    @keyframes g {
      from {clip-path:inset(0 0 0 20%);transform-origin:20% 0;}
      50%, to {clip-path:inset(0 0 0 100%);transform-origin:100% 0;}
    }
  }
  
  animation:h 1s both;
  transform-origin: center bottom;
  @keyframes h {
    from {transform:rotate(-50deg)}
    to {transform:rotate(-40deg)}
  }
}


/*button cta 1*/
button {
  margin: 15px;
}
.custom-btn {
  width: 225px;
  height: 50px;
  color: #fff;
  border-radius: 5px;
  font-weight: normal;
  font-size: 1.5rem;
  background: transparent;
  cursor: pointer;
  transition: all 0.3s ease;
  position: relative;
  display: inline-block;
   box-shadow:inset 2px 2px 2px 0px rgba(255,255,255,.5),
   7px 7px 20px 0px rgba(0,0,0,.1),
   4px 4px 5px 0px rgba(0,0,0,.1);
  outline: none;
}

.btn-16 {
  border: none;
  color: #000;
}
.btn-16:after {
  position: absolute;
  content: "";
  width: 0;
  height: 100%;
  top: 0;
  left: 0;
  direction: rtl;
  z-index: -1;
  box-shadow:
   -7px -7px 20px 0px #fff9,
   -4px -4px 5px 0px #fff9,
   7px 7px 20px 0px #0002,
   4px 4px 5px 0px #0001;
  transition: all 0.3s ease;
}
.btn-16:hover {
  color: #000;
}
.btn-16:hover:after {
  left: auto;
  right: 0;
  width: 100%;
}
.btn-16:active {
  top: 2px;
}


</style>