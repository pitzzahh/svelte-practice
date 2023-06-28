<script lang="ts">
  import { FeedbackStore } from "../stores";
  import { scale, fade } from "svelte/transition";
  import FeedBackItem from "./FeedBackItem.svelte";
</script>

{#each $FeedbackStore as feedback}
  <div in:scale out:scale={{ duration: 400 }}>
    <FeedBackItem item={feedback}/>
  </div>
{/each}
