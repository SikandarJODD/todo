<script>
  import { createEventDispatcher } from "svelte";

  let dispatch = createEventDispatcher();

  let user = {
    title: "",
    message: "",
  };
  let handleSubmit = () => {
    dispatch("formSubmitted", user);
    user.title = "";
    user.message = "";
  };
</script>

<main>
  <form on:submit|preventDefault={handleSubmit}>
    <div>
      <label for="title">Title : </label>
      <input
        type="text"
        name="title"
        id="title"
        bind:value={user.title}
        required
      />
    </div>
    <div>
      <label for="message">Message : </label>
      <textarea
        name="message"
        id="message"
        cols="10"
        rows="3"
        bind:value={user.message}
        required
      />
    </div>
    <div class="center">
      <button type="submit">Submit</button>
    </div>
  </form>
</main>

<style>
  label {
    color: rgb(196, 196, 196);
    font-size: 1.3rem;
    font-family: Poppins, "sans-serif";
    margin: 4px 0;
    letter-spacing: 0.8px;
  }
  input,
  textarea {
    font-size: 1.2rem;
    padding: 4px;
    border-radius: 4px;
    border: 2px solid #29affc;
    font-family: Poppins, sans-serif;
    background: #3737376c;
    color: rgb(247, 250, 250);
  }

  form {
    border: 1px solid white;
    padding: 10px 15px;
    margin: 10px;
    border-radius: 9px;
  }
  form > div {
    display: flex;
    flex-direction: column;
  }
  .center {
    display: flex;
    align-items: center;
    margin-top: 10px;
  }
</style>
