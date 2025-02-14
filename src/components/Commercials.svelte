<script>
  let commercials = [
    {
      image: "images/commercials/commercial1.jpg",
      description: "Delicious Burgers!",
      price: "$9.99",
    },
    {
      image: "images/commercials/commercial2.jpg",
      description: "Crispy Nuggets!",
      price: "$5.99",
    },
    {
      image: "images/commercials/commercial4.jpg",
      description: "Fresh Sandwiches!",
      price: "$7.99",
    },
  ];

  let currentIndex = 0;

  // Automatically cycle through commercials
  setInterval(() => {
    currentIndex = (currentIndex + 1) % commercials.length;
  }, 5000); // Change slide every 5 seconds
</script>

<div class="h-screen flex flex-col bg-black text-white">
  <!-- Image (Full Screen) -->
  <img
    src="/images/commercials/commercial1.jpg" 
    alt="Commercial"
    class="w-full h-[85vh] object-cover"
  />

  <!-- Content Container (1/3 Width) -->
  <div class="w-1/3 mx-auto p-4 bg-black/80">
    <!-- Description Bubble -->
    <div class="bg-white/90 text-black p-3 rounded-lg shadow-lg mb-4">
      <p class="text-xl font-bold">{commercials[currentIndex].description}</p>
    </div>

    <!-- Price Bubble -->
    <div class="bg-yellow-400 text-black p-3 rounded-lg shadow-lg">
      <p class="text-xl font-bold">{commercials[currentIndex].price}</p>
    </div>
  </div>
</div>