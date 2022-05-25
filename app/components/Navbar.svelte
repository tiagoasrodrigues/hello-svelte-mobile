<script lang="ts">

function onButtonTap() {
  alert('Hello World!');
}
</script>

<page>
  <actionBar title="Navbar"/>
    <gridLayout>
      <button text="Click me" on:tap="{onButtonTap}" />
    </gridLayout>
</page>
