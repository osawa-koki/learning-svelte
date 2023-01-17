<script lang="ts">
  import pages from '../pages';

  export let state: number;
  export let SetState: (a: number) => void;
</script>

<div id="Menu">
  {#each pages as page}
    <button on:click={() => {SetState(page.index)}} class={`${state === page.index ? 'active' : ''}`}>{page.name}</button>
  {/each}
</div>

<style lang="scss">
#Menu {
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  width: 200px;
  background-color: #1995AD;
  display: flex;
  flex-direction: column;
  padding: 1.5rem;
  button {
    margin-top: 0.5rem;
    background-color: transparent;
    border: none;
    color: white;
    text-align: left;
    padding: 0.5rem 1rem;
    &.active {
      background-color: #A1D6E2;
      color: black;
      border-radius: 0.5rem;
    }
  }
}
</style>
