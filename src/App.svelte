<script lang="ts">
  import FeedbackForm from "./components/FeedbackForm.svelte";
  import FeedbacksStats from "./components/FeedbacksStats.svelte";
  import FeedbackList from "./components/FeedbackList.svelte";

  let feedbacks: Array<any> = [
    {
      id: 1,
      rating: 10,
      text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla vel nisl",
    },
    {
      id: 2,
      rating: 8,
      text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla vel nisl",
    },
    {
      id: 3,
      rating: 6,
      text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla vel nisl",
    },
  ];

  const deleteFeedback = (e: any) => {
    const itemId = e.detail;
    feedbacks = feedbacks.filter((item) => item.id !== itemId);
  };

  $: ratingCount = feedbacks.length;
  $: averageRating =
    ratingCount == 0
      ? 0
      : feedbacks.reduce((a, item) => a + item.rating, 0) / ratingCount;
</script>

<main class="container">
  <FeedbackForm />
  <FeedbacksStats {ratingCount} {averageRating} />
  <FeedbackList {feedbacks} on:delete-feedback={deleteFeedback} />
</main>
