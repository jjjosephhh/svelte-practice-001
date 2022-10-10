<script>
  import {onDestroy} from 'svelte';
  import {FeedbackStore} from './stores';
  import FeedbackList from './components/FeedbackList.svelte';
  import FeedbackStats from './components/FeedbackStats.svelte';
  import FeedbackForm from './components/FeedbackForm.svelte';
  let feedback = [];
  const unsubscribe = FeedbackStore.subscribe(data => feedback = data);
  onDestroy(() => unsubscribe());
  $: count = feedback.length;
  $: average = feedback.reduce((a,b) => a + b.rating, 0) / count;
</script>

<main>
  <FeedbackStats {count} {average} />
  <FeedbackForm />
  <FeedbackList/>
</main>

<style>
</style>
