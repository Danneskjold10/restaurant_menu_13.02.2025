<script lang="ts">
  import { onMount } from 'svelte';
  let currentSlide = 0;
  let currentMenu = 0;
  let showMenu = false;
  
  const slides = [
    { image: '/images/commercials/commercial1.jpg', text: 'Special Burger Deal', price: '$5.99' },
    { image: '/images/commercials/commercial2.jpg', text: 'Crispy Nuggets', price: '$3.99' },
    { image: '/images/commercials/commercial3.jpg', text: 'Tasty Sandwiches', price: '$4.99' }
  ];
  
  const menus = [
    { name: 'Burgers', items: [
      { name: 'Cheese Burger', description: 'Juicy beef patty with cheese', solo: '$4.99', menu: '$7.99' },
      { name: 'Double Burger', description: 'Two beef patties with extra cheese', solo: '$6.99', menu: '$9.99' }
    ], image: '/burger_1.jpg' },
    { name: 'Nuggets', items: [
      { name: 'Chicken Nuggets (6pcs)', description: 'Crispy golden nuggets', solo: '$3.99', menu: '$6.99' },
      { name: 'Chicken Nuggets (12pcs)', description: 'Double the nuggets!', solo: '$6.99', menu: '$9.99' }
    ], image: '/nuggets_2.jpg' },
    { name: 'Sandwiches', items: [
      { name: 'Chicken Sandwich', description: 'Crispy chicken in a soft bun', solo: '$5.49', menu: '$8.49' }
    ], image: '/sandwich_1.jpg' },
    { name: 'Assiettes', items: [
      { name: 'Mixed Grill', description: 'A plate of assorted grilled meats', solo: '$9.99', menu: '$12.99' }
    ], image: '/assiettes_3.jpg' }
  ];
  
  function nextStep() {
    if (!showMenu) {
      if (currentSlide < slides.length - 1) {
        currentSlide++;
      } else {
        showMenu = true;
        currentSlide = 0;
      }
    } else {
      if (currentMenu < menus.length - 1) {
        currentMenu++;
      } else {
        showMenu = false;
        currentMenu = 0;
      }
    }
  }
  
  onMount(() => {
    const interval = setInterval(() => {
      nextStep();
    }, 3000);
    return () => clearInterval(interval);
  });
</script>

<div class="w-screen h-screen flex flex-col items-center bg-gray-900 text-white">
  {#if !showMenu}
    <div class="relative w-full h-full flex flex-col justify-center items-center">
      <img src={slides[currentSlide].image} alt="Commercial" class="h-2/3 object-cover" />
      <div class="absolute top-5 text-3xl font-bold">{slides[currentSlide].text}</div>
      <div class="absolute bottom-5 bg-yellow-400 text-black px-4 py-2 rounded-full text-2xl">{slides[currentSlide].price}</div>
    </div>
  {:else}
    <div class="w-full h-full flex flex-col text-center">
      <h1 class="text-4xl font-bold mt-4">{menus[currentMenu].name}</h1>
      <div class="h-2/3 flex flex-col items-center">
        {#each menus[currentMenu].items as item}
          <div class="mt-4">
            <h2 class="text-3xl font-semibold">{item.name}</h2>
            <p class="text-lg">{item.description}</p>
            <div class="text-xl font-bold">Solo: {item.solo} | Menu: {item.menu}</div>
          </div>
        {/each}
      </div>
      <img src={menus[currentMenu].image} class="h-1/3 object-cover" />
    </div>
  {/if}
</div>
