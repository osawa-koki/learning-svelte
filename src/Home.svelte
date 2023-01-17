<script lang="ts">
</script>

<div>
	<h1>Hello Svelte!</h1>
  <img src="/Logo.png" alt="Logo" id="Logo" />
</div>

<style lang="scss">
@import 'bootstrap/scss/bootstrap.scss';

h1 {
  text-align: center;
  color: #ff3e00;
  text-transform: uppercase;
  font-weight: 100;
  @include media-breakpoint-down(lg) {
    font-size: 3rem;
  }
  @include media-breakpoint-up(lg) {
    font-size: 5rem;
  }
}
#Logo {
  display: block;
  margin: 3rem auto;
  width: 300px;
  max-width: 100%;
}
</style>
