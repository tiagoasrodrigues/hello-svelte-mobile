<script lang="ts">
  import Navbar from "./NavBar.svelte";
  import { navigate } from "svelte-native";
  import { Bluetooth } from '@nativescript-community/ble';

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

  var bluetooth = new Bluetooth();

  bluetooth.isBluetoothEnabled().then(
    function (enabled) {
      console.log("Enabled? " + enabled);
    }
  );

  bluetooth.startScanning({
    filters: [{ serviceUUID: '180d' }],
    seconds: 4,
    onDiscovered: function (peripheral) {
      console.log("Peripheral found with UUID: " + peripheral.UUID);
    }
  }).then(function () {
    console.log("scanning complete");
  }, function (err) {
    console.log("error while scanning: " + err);
  });
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
</style>