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
  
  <div class="h-screen flex flex-col justify-between bg-black text-white p-8">
    <!-- Top Section: Menu Items -->
    <div class="w-full">
      <h1 class="text-4xl font-bold mb-6">{menus[currentCategoryIndex].category}</h1>
      {#each menus[currentCategoryIndex].items as item}
        <div class="flex justify-between items-start mb-6">
          <!-- Left Side: Name and Description -->
          <div class="w-1/2">
            <h2 class="text-2xl font-semibold">{item.name}</h2>
            <p class="text-xl">{item.description}</p>
          </div>
  
          <!-- Right Side: Solo and Menu Prices -->
          <div class="w-1/2 flex justify-end gap-8">
            <!-- Solo Price -->
            <div class="text-right">
              <div class="text-2xl font-semibold">Solo</div>
              <div class="text-xl">{item.priceSolo}</div>
            </div>
  
            <!-- Menu Price -->
            <div class="text-right">
              <div class="text-2xl font-semibold">Menu</div>
              <div class="text-xl">{item.priceMenu}</div>
            </div>
          </div>
        </div>
      {/each}
    </div>
  
    <!-- Bottom Section: Category Image -->
    <img
      src={menus[currentCategoryIndex].image}
      alt={menus[currentCategoryIndex].category}
      class="w-full h-[30vh] object-cover"
    />
  </div>