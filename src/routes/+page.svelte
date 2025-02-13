<script>
    import Commercials from "../components/Commercials.svelte";
    import MenuList from "../components/MenuList.svelte";
  
    let showCommercials = true;
  
    // Switch between commercials and menu after 15 seconds
    setInterval(() => {
      showCommercials = !showCommercials;
    }, 15000);
  </script>
  
  <div class="h-screen w-screen overflow-hidden">
    {#if showCommercials}
      <Commercials />
    {:else}
      <MenuList />
    {/if}
  </div>