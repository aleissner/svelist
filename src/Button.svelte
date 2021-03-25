<script>
  export let fab = false;
  export let icon = false;
  export let color = 'var(--color-primary)';
</script>

<button
  type="button"
  class:fab
  class:icon
  on:click
  on:keyup
  style={`background-color: ${color}`}
>
  <slot />
</button>

<style>
  button {
    border: none;
    padding: 0.5rem;
    background-color: var(--button-background-color);
  }

  button:active,
  button:focus {
    outline: none;
  }

  button:active::after {
    position: absolute;
    background-color: rgb(0 0 0 / 20%);
    content: '';
    width: 100%;
    height: 100%;
    display: inline-block;
    top: 0;
    left: 0;
    border-radius: inherit;
  }

  button.icon {
    width: 32px;
    height: 32px;
  }

  button.fab {
    color: white;
    width: 48px;
    height: 48px;
    border-radius: 50%;
    position: fixed;
    right: 1rem;
    bottom: 1rem;
    box-shadow: var(--elevation);
  }
</style>
