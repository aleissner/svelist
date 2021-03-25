<script>
import { createEventDispatcher } from 'svelte';
import { mdiClose } from '@mdi/js';
import Button from './Button.svelte';
import MDI from './MDI.svelte';

const dispatch = createEventDispatcher();

export let content = '';
export let index;

function removeItem() {
  dispatch('remove', { index });
}
</script>

<li>
  {content}
  <Button icon color="rgb(255 255 255 / 15%)" on:click={removeItem}>
    <MDI path={mdiClose} />
  </Button>
</li>

<style>
  li {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0.5rem 0 0.5rem 1rem;
  }

  li:nth-of-type(2n) {
    background-color: rgb(120 120 120 / 7%);
  }

  li:nth-of-type(2n-1) {
    background-color: rgb(66 66 66 / 12%);
  }
</style>
