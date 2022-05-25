<script lang="ts">
  import Navbar from "./NavBar.svelte";
  import { navigate } from "svelte-native";
</script>

<page>
    <actionBar flat="true">
        <stackLayout orientation="horizontal">
            <label text="Home" fontSize="24" verticalAlignment="middle" />
            <label text="About" fontSize="24" verticalAlignment="middle" />
        </stackLayout>
    </actionBar>

  <stackLayout>
    <button
      text="Navbar"
      on:tap={() => navigate({ page: Navbar })}
    />
    <stackLayout />
  </stackLayout>
  </page>

<style>
 
</style>
