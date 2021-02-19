<template>
  <div class="container flex min-h-screen h-full w-full justify-center my-8">
    <div class="w-1/4 mr-4">
      <filters @change="onChangeFilter"/>
    </div>
    <div class="w-3/4 min-h-screen ml-4">
      <div>
        <a href="#" class="back_link">
          <img src="../assets/images/icon_left.png" class="icon_back" alt="" />
          Back to Engagment Rings
        </a>
        <p class="text-xl font-semibold my-2">Select Your Diamond</p>
        <p class="text-sm text-filter_price_color">18ct White Gold Round Brilliant Simplicity Engagement Ring</p>
      </div>
      <tool-bar />
      <div class="flex flex-wrap justify-between">
        <ring-item
          v-for="(item, idx) in rings"
          :key="idx"
          :ring="item"
        />
        <div v-if="enableLastItem" class="ring_last_empty" />
      </div>
    </div>
  </div>
</template>

<script>
import Filters from "./Filter.vue";
import ToolBar from "./ToolBar.vue";

import rings_data from "./ring_dummy";
import RingItem from "./RingItem.vue";
export default {
  name: "Rings",
  components: {
    Filters,
    ToolBar,
    RingItem
  },
  data: () => ({
    rings: rings_data,
  }),
  methods: {
    onChangeFilter(filter) {
      let temp_rings = [];
      if(filter.price) {
        temp_rings = rings_data.reduce( (prev, item) => {
          if(item.price >= filter.price[0] && item.price <= filter.price[1])
            prev.push(item)
          return prev
        }, [])
      }
      this.rings = temp_rings
    }
  },
  computed: {
    enableLastItem: function () {
      if(this.rings.length % 3 === 2) return true
      return false
    }
},

}
</script>
<style scoped>
.back_link {
  @apply flex;
  @apply items-center;
  @apply text-rings_back_link_color;
  font-size: 13px
}
.icon_back {
  @apply mr-2;
  width: auto;
  height: 14px;
}
.ring_last_empty {
  width: 291px;
}
</style>
