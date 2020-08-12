<script>
  export let when = false;
  export let component;

  let loading;

  $: if (when) {
    load();
  }

  function load() {
    loading = import(component);
  }
</script>

{#if when}
  {#await loading then { default: Component }}
    <Component />
  {/await}
{/if}