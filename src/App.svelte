<script>

  import { onMount } from 'svelte';
  import ContainerItems from './lib/container_items.svelte';
  import Footer from './lib/footer.svelte';

  let items = [];
  let show = false;

  onMount(async () => {
    const res = await fetch('/src/assets/projects.json');
    items = await res.json();
  });
</script>

<main class="pt-2.5 px-2.5 pb-8">
    
    <div class="sticky top-0 relative z-10">
        <h1 class="text-2xl">Federico Petrucci</h1>
    </div>

    <div class="mb-8 lg:max-w-3/4">
      <p>
        Ciao! Sono uno sviluppatore front-end con una passione per il design digitale e le tecnologie web. Attivo dal 2020, ho lavorato su progetti complessi unendo precisione tecnica, creatività e attenzione all’esperienza utente. La mia formazione artistica e multimediale mi permette di approcciare lo sviluppo con una visione unica, bilanciando funzionalità ed estetica.
        {#if !show }<button class="inline underline cursor-pointer" on:click={()=>{show=!show}}>Leggi di più</button>{/if}
        {#if show }
            Specializzato in HTML, CSS, JavaScript, Svelte, PHP e framework come Tailwind e Alpine.js, mi piace creare interfacce performanti e intuitive. Lavoro con strumenti moderni come Vite, Docker e Git, e ho esperienza con CMS come WordPress e OctoberCMS.
            Oltre al codice, credo nell’importanza del lavoro di squadra, nella comunicazione chiara e nella continua crescita professionale. Fuori dallo schermo, sono un lettore curioso, un volontario nel doposcuola per bambini e un appassionato di stili di vita attivi e bilanciati.
        {/if}
      </p>
    </div>

    <div class="grid grid-cols-4 gap-4">
      {#each items as item}
        <ContainerItems {item} />
      {/each}
    </div>

</main>
    <Footer />
