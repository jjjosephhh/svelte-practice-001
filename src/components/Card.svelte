<script>
  import {FeedbackStore} from '../stores';
  export let itemId;

  const deleteItem = () => {
    FeedbackStore.update(cur => cur.filter(f => f.id !== itemId));
  };
</script>

<div class="card mt-4 ml-4 mr-4">
  <div class="card-content">
    <div class="content">
      <slot/>
    </div>
  </div>
  <footer class="card-footer">
    <a on:click={deleteItem} class="card-footer-item">Delete</a>
  </footer>
</div>
