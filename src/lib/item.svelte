<script>
    export let project;
</script>
<li>
  {#if project.status === "in_progress"}
    <span class="animate-pulse">(In sviluppo)</span>
    <span class="underline">{project.title}</span>. {project.description}
  {:else}
    {#if project.status === "artistic"}<span
        class="animate-pulse text-orange-500">(Progetto artistico)</span
      >{/if}
    <a href={project.url} target="_blank" class="underline text-blue-500"
      >{project.title}</a
    >. {project.description}
  {/if}

  {#if project.role}
    <p><strong>Ruolo →</strong> {project.role}.</p>
  {/if}

  {#if project.tecnologies}
    <p>
      <strong>Tecnologie → </strong>{project.tecnologies}.
    </p>
  {/if}

  {#if project.team.name}
    <p>
      <strong>Team → </strong><a href={project.team.url} class="underline"
        >{project.team.name}</a
      >
    </p>
  {/if}
</li>
