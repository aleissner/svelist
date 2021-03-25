<script>
import { mdiPlusThick } from '@mdi/js';
import storage from './storage';
import Button from './Button.svelte';
import Item from './Item.svelte';
import ItemInput from './ItemInput.svelte';
import MDI from './MDI.svelte';

const storageId = 'list';

let list = JSON.parse(storage.getItem(storageId)) || [];
let editInput = '';
let editMode = false;

function addItem() {
  editMode = false;
  if (editInput.length > 0) {
    list = [...list, editInput];
    editInput = '';
    storage.setItem(storageId, JSON.stringify(list));
  }
}

function cancelEdit() {
  editMode = false;
  editInput = '';
}

function removeItem({ detail }) {
  list.splice(detail.index, 1);
  list = list;
  storage.setItem(storageId, JSON.stringify(list));
}

function prepareNewItem() {
  if(editMode === true) {
    addItem();
    return;
  }
  editMode = true;
}
</script>

<ul>
  {#each list as item, index}
    <Item content={item} {index} on:remove={removeItem} />
  {/each}
  {#if editMode}
    <ItemInput on:submit={addItem} on:cancel={cancelEdit} bind:input={editInput} />
  {/if}
</ul>

<Button fab on:click={prepareNewItem}>
  <MDI path={mdiPlusThick} />
</Button>

<style>
  ul {
    list-style-type: none;
    padding: 0;
    margin-block-start: 0;
    margin-block-end: 0;
  }
</style>
