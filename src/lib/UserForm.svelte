<script>
  import { createEventDispatcher } from "svelte";
  let dispatch = createEventDispatcher();

  let user = {
    title: "",
    message: "",
  };
  let handleUser = (e) => {
    dispatch("Dost",user);
    user.title="";
    user.message="";
  };
</script>

<div class="form">
  <h1>Create Todo-Fodo</h1>
  <form class="" on:submit|preventDefault={handleUser}>
    <div class="mb-3">
      <label for="name" class="form-label">Title:</label>
      <input type="text" class="form-control" id="input" autocomplete="off" required bind:value={user.title}>
    </div>
    <div class="mb-3">
      <label for="about" class="form-label">Message:</label>
      <input type="text" class="form-control" id="input" autocomplete="off" required bind:value={user.message}>
    </div>
    <div class="text-center">
      <button type="submit" class="btn btn-primary ">Submit</button>
    </div>
  </form>
</div>

<style lang="scss">
    .form{
        border: 2px solid white;
        padding: 20px;
        border-radius: 10px;
        background: white;
        border: 2px solid darkblue;
        color: darkblue;
        h1{
          text-align: center;
            color: rgb(152, 224, 248);
            text-shadow:2px 2px 2px darkblue ;
        }

        #input{
            border:1px solid darkblue;

        }

        .btn{
            background: rgb(152, 224, 248);
            border: none;
            align-items: center;

            
            &:hover{
                box-shadow: 2px 2px darkblue;
                color: darkblue;
            }
        }
    }
</style>

