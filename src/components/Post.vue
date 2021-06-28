<template>
<div id="post">
   <header>
      <h3>{{ data }}</h3>
      <span @click="liked = !liked">
         <img v-if="liked"  src="../assets/liked.svg" alt="Gostei">
         <img v-else  src="../assets/like.svg" alt="" >
      </span>
   </header>
   <h1>{{ titulo }}</h1>
   <p>{{ conteudo }}</p>
</div>
</template>

<script>
export default {
   data: () => ({ liked: false }),
   props: [ 'data', 'titulo', 'conteudo'  ]
}
</script>

<style lang="scss">
#post{
   background: #FFFFFF;
   box-shadow: 0px 0px 10px rgba(19, 19, 31, 0.075);
   border-radius: 5px;

   padding: 32px;

   margin-top: 48px;

   header{
      display: flex;
      justify-content: space-between;

      > span{
         width: 24px;
         height: 24px;

         img{
            cursor: pointer;

            transition: transform 0.25s;
            transform: scale(1,1);
         }

         &:hover{
            img{
               transform: scale(1.4,1.4);
            }
         }
      }
   }


   h3{
      font-size: 16px;
      color: var(--text);
      font-weight: normal;
   }

   h1{
      font-weight: normal;
      font-size: 26px;
      color: var(--title);

      margin-top: 16px;
      margin-bottom: 4px;
   }

   p{
      font-weight: normal;
      font-size: 16px;
      line-height: 32px;
      color: var(--text);
   }
}
</style>