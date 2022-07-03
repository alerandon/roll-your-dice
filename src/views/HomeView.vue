<script>
export default {
  data() {
    return {
      formula: "",
      result: "",
      calculation: ""
    }
  },
  methods: {
    dice(diceType) {
      if (this.formula.includes(diceType)) {
        let pos = this.formula.lastIndexOf(diceType);
        let quantity = this.formula.charAt(pos - 1);
        let slice = this.formula.slice(pos - 1, pos + 3);
        console.log(slice);

        this.formula = this.formula.replace(quantity, String(Number(quantity) + 1));
      }
      else if (this.formula) {
        this.formula = this.formula.concat(' + 1' + diceType);
      }
      else {
        this.formula = this.formula.concat('1' + diceType);
      }

    },

    clear() {
      this.formula = "";
    },

    roll() {
      alert("Roll dices in development, stay tuned for updates...");
    }
  }
}
</script>

<template>
  <main class="pt-24 px-5">
    <div id="calculator" class="w-3/6 mx-auto">
      <div class="w-full flex space-x-7 items-center justify-center">
        <button @click="dice('d4')">
          <img src="src\assets\icons\dices\d4.png" alt=" " />
        </button>
        <button @click="dice('d6')">
          <img src="src\assets\icons\dices\d6.png" alt=" " />
        </button>
        <button @click="dice('d8')">
          <img src="src\assets\icons\dices\d8.png" alt=" " />
        </button>
        <button @click="dice('d10')">
          <img src="src\assets\icons\dices\d10.png" alt=" " />
        </button>
        <button @click="dice('d12')">
          <img src="src\assets\icons\dices\d12.png" alt=" " />
        </button>
        <button @click="dice('d20')">
          <img src="src\assets\icons\dices\d20.png" alt=" " />
        </button>
      </div>
      <div
        class="bg-yellow-300 w-full h-20 max-w-2xl mx-auto border rounded-xl overflow-x-auto mt-6 py-1 flex items-center justify-center">
        <p class="text-4xl">{{ formula }}</p>
      </div>
      <div class="flex justify-center pt-5">
        <button @click="clear" class="w-24 text-white text-center text-xl py-1 bg-gray-500 border rounded-md">
          Clear
        </button>
        <button @click="roll" class="w-24 text-white text-center text-xl py-1 ml-2 bg-yellow-600 border rounded-md">
          Roll
        </button>
      </div>
      <div class="text-center pt-20">
        <h3 class="text-7xl">{{ result }}</h3>
        <p class="pt-4">{{ calculation }}</p>
      </div>
    </div>
  </main>
</template>
