<script>

export default {
  data() {
    return {
      formula: "",
      result: "",
      calculation: {
        dices: "",
        numbers: "",
      },
      dices: {
        d4: 0,
        d6: 0,
        d8: 0,
        d10: 0,
        d12: 0,
        d20: 0,
      }
    }
  },
  methods: {
    dice(diceType) {
      if (this.formula.includes(diceType)) {
        const pos = this.formula.indexOf(diceType);
        const startPos = pos - this.dices[diceType].toString().length;
        const endPos = pos + diceType.length;
        const slice = this.formula.slice(startPos, endPos);

        this.dices[diceType]++;
        this.formula = this.formula.replace(slice, this.dices[diceType] + diceType);
      }
      else if (this.formula) {
        this.dices[diceType]++;
        this.formula = this.formula.concat(' + ' + this.dices[diceType] + diceType);
      }
      else {
        this.dices[diceType]++;
        this.formula = this.formula.concat(this.dices[diceType] + diceType);
      }
    },

    clear() {
      this.result = "";
      this.formula = "";

      for (const dice in this.dices) {
        this.dices[dice] = 0;
      }
    },

    roll() {
      let total = 0;

      for (const dice in this.dices) {
        if (this.dices[dice] > 0) {
          for (let i = 1; i <= this.dices[dice]; i++) {
            total += (Math.floor(Math.random() * parseInt(dice.slice(1))) + 1);
          }
        }
      }

      this.result = total.toString();
      this.calculation.dices = this.formula;
    }
  },

  computed: {
    calculatedFormula() {
      return this.result ? (this.calculation.dices + ' = ' + this.calculation.numbers) : '';
    }
  }
}
</script>

<template>
  <main class="pt-24 px-5">
    <div id="calculator" class="w-11/12 sm:w-10/12 lg:w-8/12 xl:w-6/12 mx-auto">
      <div class="w-full flex flex-wrap items-center justify-center">
        <button class="mx-2 sm:mx-4" @click="dice('d4')">
          <img class="w-10 md:w-12 h-10 md:h-12" src="src\assets\icons\dices\d4.png" alt=" " />
        </button>
        <button class="mx-2 sm:mx-4" @click="dice('d6')">
          <img class="w-10 md:w-12 h-10 md:h-12" src="src\assets\icons\dices\d6.png" alt=" " />
        </button>
        <button class="mx-2 sm:mx-4" @click="dice('d8')">
          <img class="w-10 md:w-12 h-10 md:h-12" src="src\assets\icons\dices\d8.png" alt=" " />
        </button>
        <button class="mx-2 sm:mx-4" @click="dice('d10')">
          <img class="w-10 md:w-12 h-10 md:h-12" src="src\assets\icons\dices\d10.png" alt=" " />
        </button>
        <button class="mx-2 sm:mx-4" @click="dice('d12')">
          <img class="w-10 md:w-12 h-10 md:h-12" src="src\assets\icons\dices\d12.png" alt=" " />
        </button>
        <button class="mx-2 sm:mx-4" @click="dice('d20')">
          <img class="w-10 md:w-12 h-10 md:h-12" src="src\assets\icons\dices\d20.png" alt=" " />
        </button>
      </div>
      <div
        class="bg-yellow-300 w-full h-16 max-w-2xl mx-auto border rounded-xl overflow-x-auto mt-6 py-1 flex items-center justify-center">
        <p class="text-center text-2xl lg:text-3xl">{{ formula }}</p>
      </div>
      <div class="flex justify-center pt-5">
        <button @click="clear"
          class="w-24 text-white text-center text-lg font-medium py-1 bg-gray-500 border rounded-md">
          Clear
        </button>
        <button @click="roll"
          class="w-24 text-white text-center text-lg font-medium py-1 ml-2 bg-yellow-600 border rounded-md">
          Roll
        </button>
      </div>
      <div class="text-center pt-20">
        <h3 class="text-xl md:text-4xl lg:text-7xl">{{ result }}</h3>
        <p class="pt-4">{{ calculatedFormula }}</p>
      </div>
    </div>
  </main>
</template>
