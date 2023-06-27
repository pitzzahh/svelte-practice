<script lang="ts">
    export let ratingCount: number
    export let averageRating: number
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