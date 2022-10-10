<script>
  export let count;
  export let average;
  $: avg = average ? Math.round(average * 100) / 100 : 0;
</script>

<section class="hero is-link">
  <div class="hero-body">
    <p class="title">
      Feedback Stats
    </p>
    <p class="subtitle">{count} Ratings, Average Rating: {avg}</p>
  </div>
</section>
