<script lang="ts">
  import { FeedbackStore } from "../stores";
  import Card from "./Card.svelte";
  export let item: any;


  const deleteFeedback = (itemId: number) => {
    FeedbackStore.update((value: any[]) => value.filter((item: { id: number; }) => item.id !== itemId))
  };
</script>

<Card>
  <div class="num-display">
    {item.rating}
  </div>

  <button  class="close" type="button" title="Remove Item Button" on:click={() => deleteFeedback(item.id)}>
    <svg
     
      xmlns="http://www.w3.org/2000/svg"
      viewBox="0 0 16 16"
      width="20"
      height="20"
    >
      <path
        d="M2.75 2.042969L2.042969 2.75L2.398438 3.101563L7.292969 8L2.042969 13.25L2.75 13.957031L8 8.707031L12.894531 13.605469L13.25 13.957031L13.957031 13.25L13.605469 12.894531L8.707031 8L13.957031 2.75L13.25 2.042969L8 7.292969L3.101563 2.398438Z"
        fill="#000"
      />
    </svg>
  </button>

  <p class="text-display">{item.text}</p>
</Card>

<style>
  .num-display {
    position: absolute;
    top: -10px;
    left: -10px;
    width: 50px;
    height: 50px;
    background-color: #ff6a95;
    color: #fff;
    border: 1px #eee solid;
    border-radius: 50%;
    padding: 10px;
    text-align: center;
    font-size: 19px;
  }

  .close {
    position: absolute;
    top: 10px;
    right: 20px;
    cursor: pointer;
    background: none;
    border: none;
  }
</style>
