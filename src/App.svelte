<script lang="ts">
  import { onMount } from 'svelte';
  import setting from '../setting';
  import pages from '../pages';
  import Menu from './Menu.svelte';
  import Home from './Home.svelte';
  import About from './About.svelte';
  import Contact from './Contact.svelte';
  import Info from './Info.svelte';

  let state = 0;
  function SetState(_state: number) {
    state = _state;
    const pageName = pages.find((page) => page.index === state).name;
    SetPage(pageName);
  }

  function SetPage(name: string) {
    history.pushState(null, '', `?page=${name}`);
  }

  onMount(() => {
    const urlParams = new URLSearchParams(window.location.search);
    const pageName = urlParams.get('page');
    if (pageName) {
      const page = pages.find((page) => page.name === pageName);
      if (page) {
        state = page.index;
      }
    }
  });
</script>

<svelte:head>
  <base href={setting.basePath}>
</svelte:head>

<div>
  <main>
    {#if state === 0}
      <Home />
    {:else if state === 1}
      <About />
    {:else if state === 2}
      <Contact />
    {:else if state === 3}
      <Info />
    {/if}
  </main>
  <div id="MenuContainer"><Menu SetState={SetState} state={state} /></div>
</div>

<style lang="scss">
@import 'bootstrap/scss/bootstrap.scss';

main {
  padding: 1rem;
  @include media-breakpoint-down(lg) {

  }
  @include media-breakpoint-up(lg) {
    position: relative;
    left: 100px;
    max-width: 800px;
    margin: 0 auto;
  }
}
#MenuContainer {
  @include media-breakpoint-down(lg) {
    &:not(.on) {
      display: none;
    }
  }
  @include media-breakpoint-up(lg) {
  }
}
</style>
