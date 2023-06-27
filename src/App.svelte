<script lang="ts">
  import { createEventDispatcher } from "svelte"
  import FeedbackForm from "./components/FeedbackForm.svelte"
  import FeedbacksStats from "./components/FeedbacksStats.svelte"
  import FeedbackList from "./components/FeedbackList.svelte"

  const dispatch = createEventDispatcher()

  let feedbacks: Array<any> = []

  const addFeedback = (e: CustomEvent<any>) => (feedbacks = [...feedbacks, e.detail])

  const deleteFeedback = (e: CustomEvent<any>) => (feedbacks = feedbacks.filter((item) => item.id !== e.detail))

  $: ratingCount = feedbacks.length;
  $: averageRating =
    ratingCount == 0
      ? 0
      : feedbacks.reduce((a, item) => a + item.rating, 0) / ratingCount;
</script>

<main class="container">
  <h1 style="text-align: center; color: #e8e8e8;">Feedback Form</h1>
  <FeedbackForm on:add-feedback={addFeedback} />
  <FeedbacksStats {ratingCount} {averageRating} />
  <FeedbackList {feedbacks} on:delete-feedback={deleteFeedback} />
</main>
