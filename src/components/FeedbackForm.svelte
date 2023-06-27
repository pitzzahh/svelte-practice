<script lang="ts">
  import { v4 as uuidv4 } from "uuid";
  import { createEventDispatcher } from "svelte";
  import { afterUpdate } from "svelte";
  import Card from "./Card.svelte";
  import RatingButton from "./RatingButton.svelte";
  import RatingSelect from "./RatingSelect.svelte";

  let text: string = ""
  let rating: number = 0
  let btnDisabled: boolean = true
  let errMsg: string
  let inputLength: number = 0
  const minInput: number = 10

  const dispatch = createEventDispatcher();

  afterUpdate(() => {
    inputLength = text.trim().length;
  });

  const inputObserver = () => {
    if (inputLength <= minInput - 1) {
      errMsg =
        inputLength == 0
          ? null
          : `Text must be at least ${minInput} characters`;
      btnDisabled = true
    } else {
      errMsg = null;
      btnDisabled = false
    }
  };

  const handleSelect = (e: CustomEvent<any>) => (rating = e.detail);
  const handleSubmit = () => {
    if (text.trim().length >= minInput - 1) {
      dispatch("add-feedback", { id: uuidv4(), text, rating: +rating })
      text = ''
    }
  };
</script>

<Card>
  <header>
    <h2>How would you rate our service?</h2>
  </header>
  <form on:submit|preventDefault={handleSubmit}>
    <RatingSelect on:select-rating={handleSelect} />
    <div class="input-group">
      <input
        type="text"
        bind:value={text}
        on:input={inputObserver}
        placeholder="Tell us something about your experience..."
      />
      <RatingButton type="submit" disabled={btnDisabled}>Send</RatingButton>
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
