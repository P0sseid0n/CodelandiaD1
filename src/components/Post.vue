<template>
<div id="post">
   <header><h3>{{ data }}</h3> <img src="../assets/like.svg" alt="Gostei"></header>
   <h1>{{ titulo }}</h1>
   <p>{{ conteudo }}</p>
</div>
</template>

<script>
export default {
   props: [ 'data', 'titulo', 'conteudo'  ]
}
</script>

<style lang="scss">
#post{
   background: #FFFFFF;
   box-shadow: 0px 0px 10px rgba(19, 19, 31, 0.05);
   border-radius: 5px;

   padding: 32px;

   margin-top: 48px;

   header{
      display: flex;
      justify-content: space-between;
   }

   img{
      cursor: pointer;
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
      // margin-bottom: 8px;
   }

   p{
      font-weight: normal;
      font-size: 16px;
      line-height: 32px;
      color: var(--text);
   }
}
</style>