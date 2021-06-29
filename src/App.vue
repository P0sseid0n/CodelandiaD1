<template>
<div id="app">
   <header>
      <div class="container">
         
         <h1><a href="">Codelândia</a><span>blog</span></h1>
         <div id="busca">
            <img src="./assets/search.svg" alt="Lupa">
            <input type="text" placeholder="Pesquisar no blog" v-model="search">
            <img v-if="search" src="./assets/clear.svg" alt="Lupa" @click="search = '' ">
         </div>
      </div>
   </header>
   <main>
      <div class="container">
         <div v-for="post in postsFiltered" :key="post.data + post.titulo">
            <Post :data="post.data" :titulo="post.titulo" :conteudo="post.conteudo"/>
         </div>
      </div> 
   </main>
   <footer>
      <h3>Feito por <a href="https://posseidon.netlify.app/">P0sseid0n</a></h3>
   </footer>
</div>
</template>

<script>
import Post from './components/Post.vue'

export default {
   name: 'App',
   data: () => ({
      search: '',
      posts: [
         {
            data: '02 de jul, 2021',
            titulo: 'Agora é oficial: o Windows 11 está vindo',
            conteudo: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum vestibulum auctor est. Nam vitae finibus ante. Duis lobortis tellus vel diam fringilla, eu ullamcorper ex iaculis.'
         },
         {
            data: '02 de jul, 2021',
            titulo: 'Tim Berners-Lee vai leiloar código-fonte da web',
            conteudo: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum vestibulum auctor est. Nam vitae finibus ante. Duis lobortis tellus vel diam fringilla, eu ullamcorper ex iaculis. Praesent et auctor justo. Vestibulum nisl orci, lacinia venenatis leo sit amet, pulvinar tincidunt risus. Phasellus nisl dui, cursus a lectus et, interdum ullamcorper libero.'
         },
         {
            data: '02 de jul, 2021',
            titulo: 'Tem Firefox no pedaço e você vai querer migrar',
            conteudo: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum vestibulum auctor est.'
         },
         {
            data: '02 de jul, 2021',
            titulo: 'John McAfee, criador do antivírus McAfee, morre',
            conteudo: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum vestibulum auctor est. Nam vitae finibus ante. Duis lobortis tellus vel diam fringilla, eu ullamcorper ex iaculis. Praesent et auctor justo. Vestibulum nisl orci, lacinia venenatis leo sit amet, pulvinar tincidunt risus. Phasellus nisl dui, cursus a lectus et, interdum ullamcorper libero.'
         }
      ],
      postsFiltered: []
   }),
   components: { Post },
   watch: {
      search: function (search) {
         this.postsFiltered = this.posts.filter(post => {
            return post.titulo.toLowerCase().includes(search.toLowerCase())
         })
      }
   },
   created(){
      this.postsFiltered = this.posts
   }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500&family=Lexend+Deca&display=swap');

:root {
  --blue: #3EA1DB;
  --blue-dark: #574AE8;
  --white: #FFF;

  --title: #313131;
  --text: #B6B6B6;
  
  --linear: linear-gradient(90deg, #574AE8 0%, #3EA1DB 100%);
}


* {
   box-sizing: border-box;
   padding: 0;
   margin: 0;

   font-family: 'Lexend Deca', sans-serif;
}

::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #E4E6E8;
}

::-webkit-scrollbar-thumb {
  background: var(--blue-dark);
}

::-webkit-scrollbar-thumb:hover {
  background: #4336D4;
}

.container{
   margin: 0 auto;

   height: 100%;

   width: 100%;
   max-width: 1200px;

   padding: 0 8%;
}

#app > header{
   background: var(--linear);
   height: 250px;

   padding: 32px 0;

   .container{
      display: flex;
      justify-content: space-between;
      flex-direction: column;
   }

   h1{
      color: white;
      display: flex;
      justify-content: space-between;
      font-size: 24px;
      font-weight: 400;

      a{
         color: white;
         text-decoration: none;
      }
   }

   #busca{
      background: rgba(255, 255, 255, 0.2);
      border-radius: 5px;

      height: 56px;

      display: flex;
      align-items: center;
      justify-content: space-between;

      padding: 0 16px;

      img:first-child{
         margin-left: 1%;
         margin-right: 16px;
      }

      img:last-child{
         margin-left: 16px;
         margin-right: 1%;

         padding: 4px;

         cursor: pointer;
      }
   }

   input{
      background: transparent;

      border: 0;
      outline: 0;

      width: calc(100% - 48px);
      height: 100%;

      font-size: 18px;
      font-family: 'Inter', sans-serif;
      font-weight: 500;
      color: white;

      &::placeholder { /* Chrome, Firefox, Opera, Safari 10.1+ */
         color: #FFFFFF;
         opacity: 0.5; /* Firefox */
      }

      &:-ms-input-placeholder { /* Internet Explorer 10-11 */
         color: #FFFFFF;
         opacity: 0.5;
      }

      &::-ms-input-placeholder { /* Microsoft Edge */
         color: #FFFFFF;
         opacity: 0.5;
      }
   }
}

main{
   background: #F3F5F7;

   padding-top: 1%;
   padding-bottom: 48px;

   min-height: 385px;
}

footer{
   border-radius: 8px 8px 0 0;
   background: #E9EBED;
   box-shadow: 0px 0px 10px rgba(19, 19, 31, 0.05);

   height: 64px;

   display: flex;
   justify-content: center;
   align-items: center;

   a{
      text-decoration: none;
      color: var(--blue-dark);

      &:hover{
         text-decoration: underline;
      }
   }
}

</style>
