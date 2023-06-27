<script lang="ts">
  import FeedBackItem from "./FeedBackItem.svelte";
  export let feedbacks: Array<any> = [];
</script>

{#each feedbacks as feedback (feedback.id)}
  <FeedBackItem item={feedback} on:delete-feedback />
{/each}