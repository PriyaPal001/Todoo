<script>
  //   import FilterUser from "./FilterUser.svelte";
  //   import User from "./User.svelte";

  import Usercard from "./Usercard.svelte";
  import UserForm from "./UserForm.svelte";

  if (localStorage.length === 0) {
    localStorage.setItem("1", "[]");
  }
  let users = JSON.parse(localStorage.getItem("1"));

  // let users = [
  //   {
  //     title: "Bro",
  //     message: "Frontend Coder",
  //   },
  //   {
  //     title: "Mint",
  //     message: "Business man",
  //   },
  // ];

  let handleForm = (e) => {
    users = [...users, { title: e.detail.title, message: e.detail.message }];
    let mint = JSON.stringify(users);
    localStorage.setItem("1", mint);

    // console.log(mint);
  };

  let filtertodo = (kit,e) => {
     users = JSON.parse(localStorage.getItem("1"));
    users = users.filter((value, i) =>i!=kit);
    let mint = JSON.stringify(users);
    localStorage.setItem("1", mint);
  };

  $: updatedtodo = users;
</script>

<div>
  <h1>TODOS</h1>
  <div class="container">
    <UserForm on:Dost={handleForm} />
  </div>
  <div />
  <div class="box">
    {#each updatedtodo as user, index}
      <Usercard userDetail={user} on:kill={() => filtertodo(index)} />
    {:else}
      <p>Empty</p>
    {/each}
  </div>
</div>

<style lang="scss">
  h1 {
    text-align: center;
    margin-top: 10px;
    font-size: 2rem;
    font-weight: bold;
  }

  .box {
    display: flex;
    flex-wrap: wrap;
  }
</style>
