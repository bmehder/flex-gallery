<script>
  import { panelData } from './data'
  import Panel from './Panel.svelte'

  function toggleOpen(e) {
    this.classList.toggle('open')
    const panels = document.querySelectorAll('div')
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

<main>
  {#each panelData as data}
    <Panel {data} on:click={toggleOpen} on:transitionend={toggleActive} />
  {/each}
</main>

<style>
  main {
    min-height: 100vh;
    overflow: hidden;
    display: flex;
  }
</style>
