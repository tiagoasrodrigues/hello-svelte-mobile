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

  <flexboxLayout flexDirection="column" backgroundColor="">
    <image src="https://i.ibb.co/QpGd7yV/delete-Outlined.png" />
    <button text="Aterro de Resíduos" on:tap={()=> navigate({ page: Navbar })}
      />
      <image src="https://i.ibb.co/x34yS32/360-24px.png" />
      <button text="SMO" on:tap={()=> navigate({ page: Navbar })}
        />
        <image src="https://i.ibb.co/g3nwmHD/Area-Chart.png" />
        <button text="Topográfico" on:tap={()=> navigate({ page: Navbar })}
          />
          <stackLayout />
  </flexboxLayout>
</page>

<style>
  * {
    background-color: #E5E5E5;
  }

  .appBar {
    background-color: #388E3C;
    margin-bottom: 50;

  }

  .appBar label {
    background-color: #388E3C;
    color: #FFF;
    font-size: 20;
  }

  button {
    color: #1B5E20;
    background-color: #E5E5E5;
    text-transform: uppercase;
  }

  image {
    width: 200;
    height: 200;
  }
</style>