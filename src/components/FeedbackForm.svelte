<script>
  import {FeedbackStore} from '../stores';
  import RatingSelect from './RatingSelect.svelte';
  let text = '';
  let message = '';
  let minLength = 10;
  let disabled = true;
  let rating = '5';

  const handleInput = () => {
    if (text.trim().length < minLength) {
      message = text ? `Must be at least ${minLength} characters.` : '';
      disabled = true;
      return;
    }
    message = '';
    disabled = false;
  };

  const handleRatingSelect = e => {
    rating = e.detail;
  };

  const handleSubmit = () => {
    if (text.trim().length < minLength) return;

    const newFeedback = {
      id: Date.now().toString(),
      text,
      rating: +rating,
    };

    FeedbackStore.update(cur => [...cur, newFeedback]);

    rating = '5';
    text = '';
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <div class="card m-4">
    <div class="card-content">
      <div class="content">
        <RatingSelect selected={rating} on:rating-select={handleRatingSelect}/>
        <input 
          bind:value={text}
          on:input={handleInput}
          class="input is-primary" 
          type="text" 
          placeholder="Primary input" 
          required>
        {#if message}
          <article class="message mt-4">
            <div class="message-header">
              <p>Error</p>
            </div>
            <div class="message-body">{message}</div>
          </article>
        {/if}
      </div>
    </div>
    <footer class="card-footer">
      <button {disabled} class="card-footer-item">
        Submit
      </button>
    </footer>
  </div>
</form>
