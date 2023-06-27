<script>
  import FeedBackItem from "./FeedBackItem.svelte";
  export let feedbacks = [];
</script>

{#each feedbacks as feedback (feedback.id)}
  <FeedBackItem item={feedback} on:delete-feedback />
{/each}