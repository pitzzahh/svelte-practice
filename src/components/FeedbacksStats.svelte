<script lang="ts">
  import { FeedbackStore } from "../stores";

  $: ratingCount = $FeedbackStore.length;
  $: averageRating =
    ratingCount == 0
      ? 0
      : ($FeedbackStore.reduce((a, item) => a + item.rating, 0) / ratingCount);

  // Check if averageRating has decimal places
  $: averageRatingFormatted =
    Number.isInteger(averageRating)
      ? averageRating // No decimal places, use the integer value
      : averageRating.toFixed(2); // Decimal places present, round to 2 decimal places
</script>

<div class="feedback-stats">
  <h4>{ratingCount} {ratingCount == 1 ? "Review" : "Reviews"}</h4>
  <h4>Average Rating: {averageRatingFormatted}</h4>
</div>

<style>
  .feedback-stats {
    display: flex;
    justify-content: space-between;
    margin: 20px 0;
    color: #fff;
  }
</style>
