<script lang="ts">
  import { onMount, onDestroy } from "svelte"
  import { FeedbackStore } from "../stores";
  import { scale, fade } from "svelte/transition";
  import FeedBackItem from "./FeedBackItem.svelte";

  // let feedbacks: Array<any> = [];

  // const subscribe = FeedbackStore.subscribe((value) => (feedbacks = value));

  // onMount(() => {
  //   fetch("http://localhost:5000/feedbacks")
  //     .then((res) => res.json())
  //     .then((data) => (feedbacks = data));
  // });

  // onDestroy(() => {
  //   subscribe()
  // });
</script>

{#each $FeedbackStore as feedback (feedback.id)}
  <div in:scale out:fade={{ duration: 300 }}>
    <FeedBackItem item={feedback}/>
  </div>
{/each}
