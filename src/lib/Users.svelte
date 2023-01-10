<script>
  import Form from "./Form.svelte";
  import User from "./User.svelte";

  if (localStorage.length === 0) {
    localStorage.setItem("1", "[]");
  }
  let usersInfo = JSON.parse(localStorage.getItem("1"));
  let formSubmitted = ({ detail }) => {
    usersInfo = [
      { title: detail.title, message: detail.message },
      ...usersInfo,
    ];
    let mint = JSON.stringify(usersInfo);
    localStorage.setItem("1", mint);
  };
  let filterUser = (kit, e) => {
    usersInfo = JSON.parse(localStorage.getItem("1"));
    usersInfo = usersInfo.filter((val, i) => i != kit);
    let mint = JSON.stringify(usersInfo);
    localStorage.setItem("1", mint);
  };

  $: updatedUsers = usersInfo;
</script>

<main>
  <div class="container">
    <div class="container">
      <Form on:formSubmitted={formSubmitted} />
    </div>
    <div class="container">
      {#each updatedUsers as item, index}
        <User userDetail={item} on:filterUser={() => filterUser(index)} />
      {/each}
    </div>
  </div>
</main>

<style>
  .container {
    display: flex;
    padding: 0px 3%;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
  }
</style>
