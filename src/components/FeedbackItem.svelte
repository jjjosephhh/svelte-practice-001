<script>
  import Card from './Card.svelte';
  export let item;
</script>

<Card itemId={item.id}>
  <span class="tag">Rating: {item.rating}</span>
  <div class="block mt-4">{item.text}</div>
</Card>


