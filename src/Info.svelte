<script lang="ts">
import { Alert, Button, Table  } from 'sveltestrap';
import setting from '../setting';

let languages = [];

function FetchData() {
  fetch(`/languages.json`)
    .then(response => response.json())
    .then(json => {
      languages = json.languages;
    });
}
</script>

<div>
	<h1>languages</h1>
  <Button color="primary" class="mt-3" on:click={() => FetchData()}>Fetch Data 💓</Button>
  <Table class="mt-3">
    <thead>
      <tr>
        <th>Framework</th>
        <th>Birthday</th>
        <th>On Trend</th>
      </tr>
    </thead>
    <tbody>
      {#each languages as language}
      <tr>
        <td>{language.name}</td>
        <td>{language.birthday}</td>
        <td>{language.on_trend ? '🚀🚀🚀' : '………………'}</td>
      </tr>
      {/each}
    </tbody>
  </Table>
</div>

<style lang="scss">
</style>
