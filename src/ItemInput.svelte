<script>
import { createEventDispatcher } from 'svelte';
import { onMount } from 'svelte';
import { mdiClose } from '@mdi/js';
import Button from './Button.svelte';
import MDI from './MDI.svelte';

const dispatch = createEventDispatcher();

export let input;
let inputElement;

onMount(() => {
  inputElement.focus();
});

function handleInput({ key }) {
  if (key === 'Enter') {
    dispatchSubmit();
  }
}

function dispatchSubmit() {
  dispatch('submit');
}

function dispatchCancel() {
  dispatch('cancel');
}
</script>

<div class="item-input">
  <input type="text" bind:value={input} on:keyup={handleInput} bind:this={inputElement} />
  <Button on:click={() => dispatch('cancel')} icon>
    <MDI path={mdiClose} />
  </Button>
</div>

<style>
  .item-input {
    width: 100%;
    display: flex;
    justify-content: space-between;
  }

  .item-input input {
    margin-right: 0.5rem;
    flex-grow: 1;
  }
</style>
