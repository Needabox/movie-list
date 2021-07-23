<template>
<!-- <header class="bg-gray-700 py-2 md:py-4">
  <router-link to="/">
    <h1 class="text-2xl md:text-4xl text-white text-center"><span class="text-blue-300 font-bold">Movies</span>List</h1>
  </router-link>
</header> -->
  <nav class="bg-gray-700 shadow" role="navigation">
    <div class="container mx-auto p-4 flex flex-wrap items-center md:flex-no-wrap">
      <div class="mr-4 md:mr-8">
        <a href="#" rel="home">
          <h1 class="text-2xl md:text-4xl text-white text-center"><span class="text-blue-300 font-bold">Movies</span>List</h1>
        </a>
      </div>
      <div class="ml-auto md:hidden">
        <button class="flex items-center px-3 py-2 border rounded" type="button" @click="open = !open">
          <svg class="h-3 w-3 bg-white" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg" >
            <title>Menu</title>
            <path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z"/>
          </svg>
        </button>
      </div>
      <div class="w-full md:w-auto md:flex-grow md:flex md:items-center " :class="[{ block: open }, { hidden: !open }]">
        <ul class="flex flex-col mt-4 -mx-4 pt-4 border-t md:flex-row md:items-center md:mx-0 md:mt-0 md:pt-0 md:mr-4 lg:mr-8 md:border-0" >
          <li>
            <a class="block px-4 py-1 md:p-2 lg:px-4 text-white" href="/" title="Link">HOME</a>
          </li>
          <li>
            <a class="block px-4 py-1 md:p-2 lg:px-4 text-white" href="https://www.omdbapi.com/" title="Link">API</a>
          </li>
          <li>
            <a class="block px-4 py-1 md:p-2 lg:px-4 text-white" href="https://muhammad-rafli.vercel.app/" title="Link">RAFLI</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <main>
    <router-view/>
  </main>
</template>

<script>
export default {
  data(){
    return {
      open: false,
    }
  }
}
</script>
<style lang="scss">

</style>
