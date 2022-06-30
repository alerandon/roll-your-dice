<script setup>
let formula = "";
</script>

<template>
  <main class="pt-24 px-5">
    <div id="calculator" class="w-3/6 mx-auto">
      <div class="w-full flex space-x-7 items-center justify-center">
        <button>
          <img src="src\assets\icons\dices\d4.png" alt=" " />
        </button>
        <button>
          <img src="src\assets\icons\dices\d6.png" alt=" " />
        </button>
        <button>
          <img src="src\assets\icons\dices\d8.png" alt=" " />
        </button>
        <button>
          <img src="src\assets\icons\dices\d10.png" alt=" " />
        </button>
        <button>
          <img src="src\assets\icons\dices\d12.png" alt=" " />
        </button>
        <button>
          <img src="src\assets\icons\dices\d20.png" alt=" " />
        </button>
      </div>
      <div
        class="bg-yellow-300 w-full h-20 max-w-2xl mx-auto border rounded-xl mt-6 py-1 flex items-center justify-center">
        <p class="text-4xl">{{ formula }}</p>
      </div>
      <div class="flex justify-center pt-5">
        <button class="w-24 text-white text-center text-xl py-1 bg-gray-500 border rounded-md">
          Clear
        </button>
        <button class="w-24 text-white text-center text-xl py-1 ml-2 bg-yellow-600 border rounded-md">
          Roll
        </button>
      </div>
      <div class="text-center pt-20">
        <h3 class="text-7xl">0</h3>
        <p class="pt-4">0d0 + 0d0 = (0 + 0) + (0 + 0)</p>
      </div>
    </div>
  </main>
</template>
