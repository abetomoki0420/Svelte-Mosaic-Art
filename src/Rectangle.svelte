<script>
  import { createEventDispatcher } from 'svelte'
  export let color = "tomato"

  const dispatch = createEventDispatcher()
  function notifyColor(){
    dispatch('notify', color )
  }

</script>

<div class="rectangle" style={"background:" + color } on:mouseover={notifyColor}></div>

<style>
  .rectangle {
    height: 20px;
    width: 20px;
    cursor: pointer;
  }
</style>
