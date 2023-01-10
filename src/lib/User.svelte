<script>
  import { createEventDispatcher } from "svelte";

  export let userDetail;
  let dispatch = createEventDispatcher();

  let filterUser = () => {
    dispatch("filterUser");
  };
</script>

<main>
  <div class="card">
    <h2>{userDetail.title}</h2>
    <p>
      {userDetail.message}
    </p>
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <img
      src="https://cdn-icons-png.flaticon.com/512/9068/9068752.png"
      alt="delete"
      width="20"
      on:click={filterUser}
    />
  </div>
</main>

<style>
  .card {
    border: 1px solid white;
    width: fit-content;
    padding: 20px;
    margin: 10px;
    border-radius: 12px;
    transition: all 0.3s ease;
    background-color: #222222;
    box-shadow: 0px 0px 7px rgb(34, 34, 34);
    position: relative;
  }
  .card:hover {
    transition: all 0.3s ease;
    background: linear-gradient(to top, #161616, transparent);
    border: 1px solid rgb(0, 238, 255);
  }
  h2 {
    font-size: 1.9rem;
    letter-spacing: 1px;
    color: rgba(64, 217, 248, 0.897);
    font-family: sans-serif;
  }
  p {
    font-size: 1.1rem;
    margin-top: 7px;
    font-family: Poppins, "sans-serif";
    color: #eee;
  }
  img {
    position: absolute;
    top: 7px;
    right: 7px;
    display: none;
    transition: all 0.3s ease;
  }
  .card:hover img {
    transition: all 0.3s ease;
    display: block;
  }
</style>
