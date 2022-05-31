<script lang="ts">
  import Navbar from "./NavBar.svelte";
  import { navigate } from "svelte-native";

  function onTapShare() {
    alert('Share!');
  }

  function onTapDelete() {
    alert('Delete!');
  }

</script>

<page>
  <actionBar title="Home">
    <actionItem on:tap="{onTapShare}" android.systemIcon="ic_menu_search" android.position="actionBar" />
    <actionItem on:tap="{onTapDelete}" android.systemIcon="ic_menu_share" android.position="actionBar" />
  </actionBar>

  <stackLayout>
    <button text="Navbar" on:tap={()=> navigate({ page: Navbar })}
      />
      <stackLayout />
  </stackLayout>
</page>

<style>

</style>