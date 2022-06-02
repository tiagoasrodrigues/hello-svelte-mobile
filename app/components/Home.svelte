<script lang="ts">
  import Navbar from "./NavBar.svelte";
  import { navigate } from "svelte-native";

  function onTapSettings() {
    alert('Settings!');
  }

  function onTapShare() {
    alert('Share!');
  }

  function onTapEdit() {
    alert('Edit!');
  }

  function onTapGoBack() {
    alert('Go back!');
  }
</script>

<page>
  <actionBar class="appBar">

    <stackLayout>
      <label text="Obra - Obra" />
    </stackLayout>

    <navigationButton on:tap="{onTapGoBack}" android.systemIcon="ic_menu_back" android.position="actionBar" />
    <actionItem on:tap="{onTapSettings}" android.systemIcon="ic_menu_preferences" android.position="actionBar" />
    <actionItem on:tap="{onTapShare}" android.systemIcon="ic_menu_share" android.position="actionBar" />
    <actionItem on:tap="{onTapEdit}" android.systemIcon="ic_menu_edit" android.position="actionBar" />
  </actionBar>

  <stackLayout>
    <button text="ATERRO DE RESÍDUOS" on:tap={()=> navigate({ page: Navbar })}
      />
      <button text="SMO" on:tap={()=> navigate({ page: Navbar })}
        />
        <button text="TOPOGRÁFICO" on:tap={()=> navigate({ page: Navbar })}
          />
          <stackLayout />
  </stackLayout>
</page>

<style>
  .appBar {
    background-color: #388E3C;
  }

  label {
    color: white;
    font-size: 20;
  }
</style>