<template>
  <div :class="`ring_item_container ${select ? 'ring_item_select': ''}`">
    <div class="flex justify-between w-full">
      <label class="mr-4">
        <input type="radio" :name="`ring_${ring.id}`" value="true" v-model="select"/>
        <span class="tool_bar_media_text">Compare</span>
      </label>
      <a href="#" class="ring_item_more_link">More Info</a>
    </div>
    <img :src=ring.image class="ring_image" alt="" />
    <span :class="`font-medium text-lg ${select ? 'text-primary': ''}`">&pound;{{ ring.price }}</span>
    <span class="text-filter_price_color">0.81ct</span>
    <button class="ring_item_btn" @click="select=!select">Choose</button>
  </div>
</template>
<script>
export default {
  data: () => ({
    select: false
  }),
  props: ['ring'],
}
</script>
<style scoped>
.ring_item_container {
  @apply flex;
  @apply flex-col;
  @apply items-center;
  @apply bg-background;
  @apply my-4;
  @apply py-2;
  @apply px-4;
  border-radius: 10px;
  width: 291px;
  height: 262px;
}
.ring_item_select {
  @apply border-1;
  @apply border-primary;
  box-shadow: 0px 0px 8px rgba(252, 131, 19, 0.4);
}
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
  border-radius: 4px;
  border-style: solid;
  border-width: 0.1rem;
  border-color: gray;
}
.tool_bar_media_text {
  @apply text-gray-700;
  @apply text-sm;
}
label > input[type="radio"]:checked + *::before {
  border-color: #e37e1b;
  background-clip: content-box;
  background-color: #e37e1b;
  padding: 2px;
}
fieldset {
  margin: 20px;
  max-width: 400px;
}
label > input[type="radio"] + * {
  display: inline-block;
}
.ring_image {
  @apply my-4;
  height: 84px;
  width: fit-content;
}
.ring_item_btn {
  @apply my-2;
  @apply bg-primary;
  @apply text-xs;
  border-radius: 10px;
  color: white;
  width: 146px;
  height: 34px;
  outline: none !important;
}
.ring_item_more_link {
  @apply text-filter_price_color;
  text-decoration: underline;
}
</style>