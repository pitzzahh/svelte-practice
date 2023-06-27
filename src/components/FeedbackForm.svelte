<script lang="ts">
  import { afterUpdate } from "svelte";
  import Card from "./Card.svelte";
  import Button from "./Button.svelte";
  import RatingSelect from "./RatingSelect.svelte";

  let text: string = "";
  let rating: number = 10;
  let btnDisabled: boolean = true;
  let errMsg: string;
  let inputLength: number = 0; 
  const minInput: number = 10;

  afterUpdate(() => {
    inputLength = text.trim().length;
  });

  const inputObserver = () => {
    if (inputLength <= minInput) {
      errMsg = `Text must be at least ${minInput} characters`;
      btnDisabled = true;
    } else {
      errMsg = null;
      btnDisabled = false;
    }
  };
</script>

<Card>
  <header>
    <h2>How would you rate our service?</h2>
  </header>

  <RatingSelect />

  <form action="">
    <!-- rating selection -->
    <div class="input-group">
      <input
        type="text"
        bind:value={text}
        on:input={inputObserver}
        placeholder="Tell us something about your experience..."
      />
      <Button type="submit" disabled={btnDisabled}>Send</Button>
    </div>
    {#if errMsg}
      <div class="message">{errMsg}</div>
    {/if}
  </form>
</Card>

<style>
  header {
    max-width: 400px;
    margin: auto;
  }

  header h2 {
    font-size: 22px;
    font-weight: 600;
    text-align: center;
  }

  .input-group {
    display: flex;
    flex-direction: row;
    border: 1px solid #ccc;
    padding: 8px 10px;
    border-radius: 8px;
    margin-top: 15px;
  }

  input {
    flex-grow: 2;
    border: none;
    font-size: 14px;
    margin: auto 2px;
  }

  input:focus {
    outline: none;
  }

  .message {
    padding-top: 10px;
    text-align: center;
    color: rebeccapurple;
  }
</style>
