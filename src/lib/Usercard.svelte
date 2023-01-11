<script>
  import { createEventDispatcher } from "svelte";
  export let userDetail;
  let dispatch = createEventDispatcher();

  let handlecut = () => {
    dispatch("kill");
  };
</script>

<div class="card">
  <h2 class="content">{userDetail.title}</h2>
  <p>{userDetail.message}</p>
  <!-- svelte-ignore a11y-click-events-have-key-events -->
  <img
    src="https://cdn-icons-png.flaticon.com/512/9351/9351526.png"
    alt="cross"
    width="25"
    on:click={handlecut}
  />
</div>

<style lang="scss">
  .card {
    border: 1px solid #000;
    padding: 10px 10px;
    width: 25%;
    display: flex;
    flex-direction: column;
    margin: 20px;
    transition: all 0.3s ease;
    position: relative;
    align-items: center;
    text-align: center;
    border-radius: 10px;
    background-color: rgb(152, 224, 248);


    img {
      position: absolute;
      display: none;
      top: 10px;
      right: 10px;
    }

    &:hover {
      box-shadow: 5px 5px rgb(2, 2, 151);
      transition: all 0.3s ease;
      color: navy;
    }
    &:hover img {
      display: block;
    }
  }
</style>
