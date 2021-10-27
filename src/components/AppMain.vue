<template>
    <div class="wrapper">
        <!--<div class="card">
            <h1 class="font-bold text-6xl">Vues With TailwindCSS</h1>
            <h2 class="text-3xl font-bold">Using VueCLI</h2>
        </div>-->
<table class="table-fixed">
  <tbody>
    <tr>
      <td class="border border-pink-500 p-8"><button>O</button></td>
      <td class="border border-pink-500 p-8"><button>X</button></td>
      <td class="border border-pink-500 p-8"><button>X</button></td>
    </tr>
    <tr>
      <td class="border border-pink-500 p-8"><button>X</button></td>
      <td class="border border-pink-500 p-8"><button>O</button></td>
      <td class="border border-pink-500 p-8"><button>O</button></td>
    </tr>
    <tr>
      <td class="border border-pink-500 p-8"><button>X</button></td>
      <td class="border border-pink-500 p-8"><button>O</button></td>
      <td class="border border-pink-500 p-8"><button>X</button></td>

    </tr>

  </tbody>
</table> 
        
    </div>
</template>

<script>
    export default {
        
    }
</script>

<style lang="postcss" scoped>
    .wrapper{
        @apply flex justify-center items-center h-screen text-emerald-500 text-center bg-gray-100 ;
    }
    .card{
        @apply rounded-lg border border-emerald-300 bg-emerald-100 p-10 shadow-lg;
    }

</style>