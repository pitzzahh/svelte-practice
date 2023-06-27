<script lang="ts">
  import { FeedbackStore } from "../stores";

  $: ratingCount = $FeedbackStore.length;
  $: averageRating =
    ratingCount == 0
      ? 0
      : $FeedbackStore.reduce((a, item) => a + item.rating, 0) / ratingCount;
</script>

<div class="feedback-stats">
  <h4>{ratingCount} Reviews</h4>
  <h4>Average Rating: {averageRating}</h4>
</div>

<style>
  .feedback-stats {
    display: flex;
    justify-content: space-between;
    margin: 20px 0;
    color: #fff;
  }
</style>
