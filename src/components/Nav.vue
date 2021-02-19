<template>
  <div>
    <div class="topbar_container">
      <div
        v-for="(item, idx) in top_bars"
        :key="idx"
        class="w-1/5 top_bar_item"
      >
        <img :src="item.image" class="top_bar_img" alt="" />
        {{ item.name }}
      </div>
    </div>
    <nav class="bg-nav_background flex justify-center">
      <div class="nav_container">
        <div class="flex-1 flex items-center">
          <div class="flex space-x-4">
            <a
              v-for="(tab, idx) in tabs"
              :key="idx"
              href="#"
              @click="changeTab(idx)"
              :class="`nav_item ${selected_tab === idx ? 'nav_item_active': ''}`"
            >
              {{ tab }}
            </a>
            <a href="#" class="nav_item nav_sale">
              Sale!
            </a>
          </div>
        </div>
        <div class="flex-1 justify-center flex items-center">
          <img src="../assets/images/nav_logo.png" alt="" />
        </div>
        <div class="flex-1 justify-end flex items-center">
          <div class="flex space-x-4">
            <a href="#" class="nav_item">
              My Account
            </a>
            <a href="#" class="nav_item flex">
              <img class="mx-2" src="../assets/images/nav_cart.png" alt="" />
              My Cart
            </a>
          </div>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  name: "Nav",
  data: () => ({
    tabs: ['Diamond', 'Rings', 'Jewellery', 'Bespoke'],
    selected_tab: 0,
    top_bars: [
      { name: 'Book a Virtual Consultation', image: require('../assets/images/icon_video.png') },
      { name: 'Contact a Specialist on WhatsApp', image: require('../assets/images/icon_whatsapp.png') },
      { name: 'Click and Collect', image: require('../assets/images/icon_click.png') },
      { name: '0800 080 3535  ', image: require('../assets/images/icon_phone.png') },
      { name: 'Store Location', image: require('../assets/images/icon_location.png') },
    ]
  }),
  methods: {
    changeTab(idx) {
      this.selected_tab = idx
    }
  }
}
</script>
<style scoped>
.topbar_container {
  @apply bg-top_bar_background;
  @apply flex;
  @apply flex-1;
  @apply items-center;
  @apply justify-between;
  @apply text-rings_back_link_color;
  height: 42px;
}
.top_bar_item {
  @apply flex;
  @apply justify-center;
  @apply items-center;
  @apply border-r-1;
  @apply border-top_bar_border;
}
.top_bar_img {
  @apply mx-2;
  width: 16px;
  height: 16px;
}
.nav_container {
  @apply container;
  @apply flex;
  @apply justify-center;
  height: 86px;
}
.nav_item {
  @apply text-nav_font_size;
  @apply text-nav_text_color;
  @apply font-sans;
  @apply px-3;
  @apply py-2;
}
.nav_item_active {
  @apply border-b-1;
  @apply border-nav_active_color;
  @apply text-white;
}
.nav_sale {
  @apply text-nav_active_color;
}
</style>
