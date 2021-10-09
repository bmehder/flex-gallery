<script>
  import { panelData } from './data'
  import Panel from './Panel.svelte'

  function toggleOpen(e) {
    this.classList.toggle('open')
    const panels = document.querySelectorAll('.panel')
    panels.forEach(panel => {
      if (panel !== this) {
        panel.classList.remove('open')
      }
    })
  }

  function toggleActive(e) {
    if (e.propertyName.includes('flex')) {
      this.classList.toggle('open-active')
    }
  }
</script>

<div class="panels">
  {#each panelData as data, index}
    <Panel
      {data}
      {index}
      on:click={toggleOpen}
      on:transitionend={toggleActive}
    />
  {/each}
</div>

<style>
  .panels {
    min-height: 100vh;
    overflow: hidden;
    display: flex;
  }
</style>
