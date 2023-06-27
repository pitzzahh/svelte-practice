<script lang="ts">
  import FeedbackForm from "./components/FeedbackForm.svelte"
  import FeedbacksStats from "./components/FeedbacksStats.svelte"
  import FeedbackList from "./components/FeedbackList.svelte"
</script>

<main class="container">
  <h1 style="text-align: center; color: #e8e8e8;">Feedback Form</h1>
  <FeedbackForm />
  <FeedbacksStats />
  <FeedbackList />
</main>
