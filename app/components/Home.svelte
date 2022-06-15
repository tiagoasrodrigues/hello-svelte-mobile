<script lang="ts">
  import Navbar from "./NavBar.svelte";
  import { navigate } from "svelte-native";
  import { Bluetooth } from '@nativescript-community/ble';
  import { Template } from 'svelte-native/components'

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

  let peripherals = ["one", 'two', 'three']

  function onPeripheralTap() {
    alert("Peripheral found with UUID: ");
  }

  var bluetooth = new Bluetooth();

  bluetooth.isBluetoothEnabled().then(
    function (enabled) {
      console.log("Enabled? " + enabled);
    }
  );


  bluetooth.startScanning({
    // filters: [{ serviceUUID: '180d' }],
    seconds: 4,
    onDiscovered: function (peripheral) {
      console.log("Peripheral found with UUID: " + peripheral.UUID);
    }
  }).then(function () {
    console.log("scanning complete");
  }, function (err) {
    console.log("error while scanning: " + err);
  });

  bluetooth.connect({
     UUID: 'EA:D8:D1:1B:29:A5',
    onConnected: function (peripheral) {
      console.log("Peripheral connected with UUID: " + peripheral.UUID);
      alert("Peripheral connected with UUID: " + peripheral.UUID);
      // the peripheral object now has a list of available services:
      peripheral.services.forEach(function (service) {
        console.log("service found: " + JSON.stringify(service));
      });
    },
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

  <listView items="{ peripherals }" on:itemTap="{onPeripheralTap}">
    <Template let:item>
      <!-- Shows the list item label in the default color and style. -->
      <label text="{item}" />
    </Template>
  </listView>
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