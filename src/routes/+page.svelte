<script lang="ts">
  import { onMount } from 'svelte';
  let currentSlide = 0;
  let currentMenu: number = 0;

  let showMenu = false;
  
  const slides = [
  { 
    image: '/images/commercials/commercial1.jpg', 
    text: 'Special Burger Deal', 
    price: '$5.99',
    description: 'Get our special burger with fresh ingredients and a soft bun!'
  },
  { 
    image: '/images/commercials/commercial2.jpg', 
    text: 'Crispy Nuggets', 
    price: '$3.99',
    description: 'Golden and crispy nuggets made from premium chicken.'
  },
  { 
    image: '/images/commercials/commercial3.jpg', 
    text: 'Tasty Sandwiches', 
    price: '$4.99',
    description: 'Enjoy our fresh sandwiches with delicious fillings!'
  }
];


  
  const menus = [
    { name: 'Burgers', items: [
      { name: 'Cheese Burger', description: 'Juicy beef patty with cheese', solo: '$4.99', menu: '$7.99' },
      { name: 'Double Burger', description: 'Two beef patties with extra cheese', solo: '$6.99', menu: '$9.99' },
      { name: 'Bacon Burger', description: 'Beef patty with crispy bacon', solo: '$5.99', menu: '$8.99' },
      { name: 'Vegan Burger', description: 'Plant-based patty with fresh veggies', solo: '$5.49', menu: '$8.49' },
      { name: 'BBQ Burger', description: 'Grilled patty with BBQ sauce', solo: '$6.49', menu: '$9.49' }
    ], image: '/burger_1.jpg' },
    { name: 'Nuggets', items: [
      { name: 'Chicken Nuggets (6pcs)', description: 'Crispy golden nuggets', solo: '$3.99', menu: '$6.99' },
      { name: 'Chicken Nuggets (12pcs)', description: 'Double the nuggets!', solo: '$6.99', menu: '$9.99' },
      { name: 'Spicy Nuggets', description: 'Hot & crispy nuggets', solo: '$4.49', menu: '$7.49' },
      { name: 'BBQ Nuggets', description: 'BBQ-flavored nuggets', solo: '$5.49', menu: '$8.49' }
    ], image: '/nuggets_2.jpg' },
    { name: 'Sandwiches', items: [
      { name: 'Chicken Sandwich', description: 'Crispy chicken in a soft bun', solo: '$5.49', menu: '$8.49' },
      { name: 'Club Sandwich', description: 'Turkey, bacon & cheese', solo: '$6.49', menu: '$9.49' },
      { name: 'Tuna Sandwich', description: 'Fresh tuna with lettuce', solo: '$4.99', menu: '$7.99' }
    ], image: '/sandwich_1.jpg' },
    { name: 'Assiettes', items: [
      { name: 'Mixed Grill', description: 'A plate of assorted grilled meats', solo: '$9.99', menu: '$12.99' },
      { name: 'Kebab Plate', description: 'Sliced kebab with rice', solo: '$8.99', menu: '$11.99' },
      { name: 'Falafel Plate', description: 'Falafel with hummus & salad', solo: '$7.49', menu: '$10.49' }
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
      <img src={slides[currentSlide].image} 
         alt={slides[currentSlide].text} 
         class="h-2/3 object-cover" />
    
    <!-- Title -->
    <div class="absolute top-5 text-3xl font-bold">{slides[currentSlide].text}</div>
  
    <!-- Description Bubble -->
    <div class="absolute bottom-16 bg-gray-800 text-white px-4 py-2 rounded-lg text-lg w-3/4 text-center shadow-lg">
      {slides[currentSlide].description}
    </div>
  
    <!-- Price Tag -->
    <div class="absolute bottom-5 bg-yellow-400 text-black px-4 py-2 rounded-full text-2xl">
      {slides[currentSlide].price}
    </div>
  </div>
  
  {:else}
  <div class="w-full h-full flex flex-col text-center">
    <h1 class="text-4xl font-bold mt-4">{menus[currentMenu].name}</h1>
    <div class="h-2/3 flex flex-col items-center w-3/4">
      <div class="flex w-full justify-between border-b pb-2 text-xl font-bold">
        <span class="w-2/4 text-left">Item</span>
        <span class="w-1/4 text-right">Solo</span>
        <span class="w-1/4 text-left ml-4">Menu</span>
      </div>
      {#each menus[currentMenu].items as item}
        <div class="flex w-full justify-between py-2 border-b">
          <span class="w-2/4 text-left">{item.name}</span>
          <span class="w-1/4 text-right">{item.solo}</span>
          <span class="w-1/4 text-left ml-4">{item.menu}</span>
        </div>
      {/each}
    </div>
    <img src={menus[currentMenu].image} class="h-1/3 object-cover" />
  </div>
  {#if !showMenu}
  <div class="relative w-full h-full flex flex-col justify-center items-center">
    <img src={slides[currentSlide].image} alt="Commercial" class="h-2/3 object-cover" />
    <div class="absolute top-5 text-3xl font-bold">{slides[currentSlide].text}</div>
    <div class="absolute bottom-5 flex flex-col items-center">
      <div class="bg-yellow-400 text-black px-4 py-2 rounded-full text-2xl">
        {slides[currentSlide].price}
      </div>
      <div class="bg-gray-800 bg-opacity-75 text-white text-lg px-3 py-1 rounded-lg mt-2">
        {slides[currentSlide].description}
      </div>
    </div>
  </div>
{/if}

  
  {/if}
</div>
