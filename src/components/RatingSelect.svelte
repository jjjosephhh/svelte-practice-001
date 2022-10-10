<script>
  import {createEventDispatcher} from 'svelte';
  export let selected = '5';
  const dispatch = createEventDispatcher();
  const onChange = e => {
    dispatch('rating-select', selected);
  };
</script>

<div class="select is-fullwidth mb-4">
  <select bind:value={selected} on:change={onChange}>
    <option on:change={onChange} value='1'>⭐</option>
    <option on:change={onChange} value='2'>⭐⭐</option>
    <option on:change={onChange} value='3'>⭐⭐⭐</option>
    <option on:change={onChange} value='4'>⭐⭐⭐⭐</option>
    <option on:change={onChange} value='5'>⭐⭐⭐⭐⭐</option>
  </select>
</div>
