<script>
    let menus = [
      {
        category: "Burgers",
        image: "burger_1.jpg",
        items: [
          {
            name: "Classic Burger",
            description: "Juicy beef patty with fresh veggies",
            priceSolo: "$8.99",
            priceMenu: "$12.99",
          },
          {
            name: "Cheese Burger",
            description: "Beef patty with melted cheese",
            priceSolo: "$9.99",
            priceMenu: "$13.99",
          },
        ],
      },
      {
        category: "Nuggets",
        image: "nuggets_2.jpg",
        items: [
          {
            name: "Chicken Nuggets",
            description: "Crispy chicken nuggets with dipping sauce",
            priceSolo: "$5.99",
            priceMenu: "$8.99",
          },
          {
            name: "Spicy Nuggets",
            description: "Spicy chicken nuggets with ranch sauce",
            priceSolo: "$6.99",
            priceMenu: "$9.99",
          },
        ],
      },
      {
        category: "Assiettes",
        image: "assiettes_3.jpg",
        items: [
          {
            name: "Meat Platter",
            description: "A mix of grilled meats with sides",
            priceSolo: "$12.99",
            priceMenu: "$18.99",
          },
          {
            name: "Veggie Platter",
            description: "Fresh veggies with dips",
            priceSolo: "$10.99",
            priceMenu: "$15.99",
          },
        ],
      },
      {
        category: "Sandwiches",
        image: "sandwich_1.jpg",
        items: [
          {
            name: "Turkey Sandwich",
            description: "Sliced turkey with lettuce and mayo",
            priceSolo: "$7.99",
            priceMenu: "$11.99",
          },
          {
            name: "Veggie Sandwich",
            description: "Fresh veggies with hummus",
            priceSolo: "$6.99",
            priceMenu: "$10.99",
          },
        ],
      },
    ];
  
    let currentCategoryIndex = 0;
  
    // Automatically cycle through menu categories
    setInterval(() => {
      currentCategoryIndex = (currentCategoryIndex + 1) % menus.length;
    }, 10000); // Change category every 10 seconds
  </script>
  
  <div class="h-screen flex flex-col bg-black text-white">
    <!-- Top Section: Menu Items -->
    <div class="w-full p-4">
      <h1 class="text-3xl font-bold mb-4">{menus[currentCategoryIndex].category}</h1>
      {#each menus[currentCategoryIndex].items as item}
        <div class="flex justify-between items-start mb-4">
          <!-- Left Side: Name and Description -->
          <div class="w-2/3">
            <h2 class="text-xl font-semibold">{item.name}</h2>
            <p class="text-lg">{item.description}</p>
          </div>
  
          <!-- Right Side: Solo and Menu Prices -->
          <div class="w-1/3 flex flex-col items-end">
            <div class="flex gap-4">
              <div class="text-xl font-semibold">Solo</div>
              <div class="text-xl font-semibold">Menu</div>
            </div>
            <div class="flex gap-4">
              <div class="text-lg">{item.priceSolo}</div>
              <div class="text-lg">{item.priceMenu}</div>
            </div>
          </div>
        </div>
      {/each}
    </div>
  
    <!-- Bottom Section: Category Image -->
    <img
      src={menus[currentCategoryIndex].image}
      alt={menus[currentCategoryIndex].category}
      class="w-full h-[40vh] object-cover"
    />
  </div>