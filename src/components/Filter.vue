<template>
  <div class="bg-background px-7 py-6 mr-2">
    <h1 class="font-medium text-lg">Filter</h1>
    <div class="flex my-8">
      <label class="mr-4">
        <input type="radio" name="resource" value="natural" checked />
        <span class="text-sm">Natural</span>
      </label>
      <label class="ml-4">
        <input type="radio" name="resource" value="lab" />
        <span class="text-sm">Lab Grown</span>
      </label>
    </div>
    <div class="my-8">
      <h2 class="font-medium text-md my-4">Price</h2>
      <vue-slider v-model="price" @change="onChange" :enable-cross="false" :max="price_max"/>
      <div class="flex justify-between">
        <span class="filter_price_text">&pound;{{ price[0] }}</span>
        <span class="filter_price_text">&pound;{{ price[1] }}</span>
      </div>
    </div>
    <div class="my-8">
      <h2 class="flex font-medium text-md my-4 items-center">
        Caret
        <img src="../assets/images/icon_info.png" class="icon_info" alt="" />
      </h2>
      <vue-slider v-model="caret" :enable-cross="false" :max="500" />
      <div class="flex justify-between">
        <span class="filter_price_text">{{ caret[0] / 100 }}</span>
        <span class="filter_price_text">{{ caret[1] / 100 }}</span>
      </div>
    </div>
    <div class="my-8">
      <h2 class="flex font-medium text-md my-4 items-center">
        Clarity
        <img src="../assets/images/icon_info.png" class="icon_info" alt="" />
      </h2>
      <div class="flex flex-wrap">
        <div v-for="(clarity, idx) in clarity_val" :key="idx" class="mr-3 my-2">
          <input type="checkbox" :id="`toggle_clarity_${idx}`" class="toggle_check" v-model="clarrity_checkable[idx]"/>
          <label :for="`toggle_clarity_${idx}`" :class="`${clarrity_checkable[idx] ? 'toggle_btn toggle_btn_select': 'toggle_btn'}`">{{clarity}}</label>
        </div>
      </div>
    </div>
    <div class="my-8">
      <h2 class="flex font-medium text-md my-4 items-center">
        Clarity
        <img src="../assets/images/icon_info.png" class="icon_info" alt="" />
      </h2>
      <div class="flex flex-wrap">
        <div v-for="(colour, idx) in colour_val" :key="idx" class="mr-3 my-2">
          <input type="checkbox" :id="`toggle_colour_${idx}`" class="toggle_check" v-model="colour_checkable[idx]"/>
          <label :for="`toggle_colour_${idx}`" :class="`${colour_checkable[idx] ? 'toggle_btn toggle_btn_select': 'toggle_btn'}`">{{colour}}</label>
        </div>
      </div>
    </div>
    <div class="flex justify-between">
      <a href="#" class="advanced_link">Show Advanced</a>
      <img src="../assets/images/icon_reset.png" class="icon_reset" alt="" />
    </div>
  </div>
</template>
<script>
import VueSlider from 'vue-slider-component'
import 'vue-slider-component/theme/antd.css'
export default {
  name: 'filters',
  components: {
    VueSlider
  },
  data: () => ({
    price_max: 2500,
    price: [],
    caret: [57, 249],
    number: 10,
    clarity_val: [
      'SI1', 'VS1', 'VS2', 'IF', 'WS2', 'WS1'
    ],
    clarrity_checkable: new Array(6).fill(false),
    colour_val: [
      'K', 'J', 'I', 'H', 'G', 'F', 'E', 'D'
    ],
    colour_checkable: new Array(8).fill(false),
    toggle: false
  }),
  mounted() {
    this.price = [0, this.price_max]
  },
  methods: {
    onChange() {
      const filter = {
        price: this.price
      }
      this.$emit('change', filter)
    }
  }
}
</script>
<style scoped>
label > input[type="radio"] {
  display: none;
}
label > input[type="radio"] + *::before {
  content: "";
  display: inline-block;
  vertical-align: bottom;
  margin-bottom: 2px;
  width: 14px;
  height: 14px;
  margin-right: 0.3rem;
  border-radius: 50%;
  border-style: solid;
  border-width: 0.1rem;
  border-color: gray;
}
label > input[type="radio"]:checked + * {
  color: #e37e1b;
}
label > input[type="radio"]:checked + *::before {
  background: radial-gradient(#e37e1b, transparent,  transparent);
  border-color: #e37e1b;
}
fieldset {
  margin: 20px;
  max-width: 400px;
}
label > input[type="radio"] + * {
  display: inline-block;
}

.filters_slider {
  @apply w-full;
  @apply relative;
  position: relative;
}
.simple-range-slider-popover {
  display: none;
}
.icon_info {
  @apply mx-2;
  width: 13px;
  height: 13px;
}
.icon_reset {
  width: 16px;
  height: 16px;
}
.toggle_check {
  display: none;
}
.toggle_btn {
  @apply cursor-pointer;
  @apply bg-white;
  @apply px-5;
  @apply py-1;
  @apply rounded-md;
  @apply border-solid;
  @apply border-1;
  @apply border-gray-200;
  font-size: 14px;
}
.toggle_btn_select {
  @apply border-primary;
  @apply text-primary;
}
.filter_price_text {
  @apply text-filter_price_color;
}
</style>
<style>
.vue-slider-process {
  background-color: #e37e1b !important;
}
.vue-slider-dot-tooltip {
  display: none;
}
.vue-slider-dot-handle {
  width: 10px;
  height: 20px;
  border-radius: 4px;
  border-color: lightgray !important;
  border-width: 0.5px;
}
.vue-slider-dot {
  width: auto !important;
  height: auto !important;
}
.advanced_link {
  @apply text-filter_price_color;
  text-decoration: underline;
}
</style>