<script>
    import { slide } from "svelte/transition";
    import Item from "./item.svelte";
    export let item;
    let show = item.closed ? false : true;
</script>          
          
<div class="lg:col-span-3 col-span-4">

  <button class="flex items-center space-x-4 cursor-pointer hover:opacity-35" on:click={()=>{show = !show}}>
      <h2 class="text-2xl pb-1">{item.year}</h2>
      <svg class="w-8 mb-2 transition-transform duration-200" class:rotate-180={show} viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <path d="M5.70711 9.71069C5.31658 10.1012 5.31658 10.7344 5.70711 11.1249L10.5993 16.0123C11.3805 16.7927 12.6463 16.7924 13.4271 16.0117L18.3174 11.1213C18.708 10.7308 18.708 10.0976 18.3174 9.70708C17.9269 9.31655 17.2937 9.31655 16.9032 9.70708L12.7176 13.8927C12.3271 14.2833 11.6939 14.2832 11.3034 13.8927L7.12132 9.71069C6.7308 9.32016 6.09763 9.32016 5.70711 9.71069Z" fill="#0F0F0F"></path> </g></svg>
  </button>

  {#if show}
    <ul class="list-disc list-outside pl-5 text-xs space-y-2 lg:pr-4" transition:slide={{ duration: 200 }}>
      {#each item.projects as project}
        <Item {project}  />
      {/each}
    </ul>
  {/if}
  
</div>