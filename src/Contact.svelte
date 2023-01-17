<script lang="ts">
import { Alert, Button, Input } from 'sveltestrap';

let count = 0;
let email = '';

const mail_regex = /^([a-zA-Z0-9_\-\.]+)@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.)|(([a-zA-Z0-9\-]+\.)+))([a-zA-Z]{2,4}|[0-9]{1,3})(\]?)$/;
function validateEmail(email) {
  return mail_regex.test(email);
}
</script>

<div>
	<h1>Dummy Contact...</h1>
  <Alert color="primary">You clicked {count} times.</Alert>
  <Button color="primary" on:click={() => count++}>Click me 💓</Button>
  <hr />
  <Input type="email" bind:value={email} placeholder="Enter your email" />
  {#if validateEmail(email)}
    <Alert color="success" class="mt-3">Valid email</Alert>
  {:else}
    <Alert color="danger" class="mt-3">Invalid email</Alert>
  {/if}
</div>

<style lang="scss">
</style>
