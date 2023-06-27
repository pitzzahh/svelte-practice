<script lang="ts">
  import {scale, fade} from "svelte/transition";
  import FeedBackItem from "./FeedBackItem.svelte";
  export let feedbacks: Array<any> = [];
</script>

{#each feedbacks as feedback (feedback.id)}
  <div in:scale out:fade={{ duration: 300 }}>
    <FeedBackItem item={feedback} on:delete-feedback />
  </div>
{/each}