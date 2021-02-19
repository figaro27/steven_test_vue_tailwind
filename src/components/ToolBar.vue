<template>
  <div class="flex my-4 py-4 justify-between border-b-1">
    <div class="relative">
      <input type="text" placeholder="Diamond ID" class="search_box">
      <img src="../assets/images/icon_search.png" class="icon_search" alt="" />
    </div>
    <div class="flex">
      <div class="border-r-1">
        <label class="mr-4">
          <input type="radio" name="media" value="image" checked />
          <span class="tool_bar_media_text">With Images</span>
        </label>
        <label class="mr-4">
          <input type="radio" name="media" value="media" />
          <span class="tool_bar_media_text">With Videos</span>
        </label>
        <label class="mr-4">
          <input type="radio" name="media" value="advanced" />
          <span class="tool_bar_media_text">Show Advanced</span>
        </label>
      </div>
      <div class="flex">
        <img src="../assets/images/icon_grid.svg" class="layout_icon" alt="" />
        <img src="../assets/images/icon_list.svg" class="layout_icon" alt="" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "tool-bar",

}
</script>
<style scoped>
.search_box {
  @apply pl-8;
  @apply pr-2;
  @apply py-1;
  @apply border-solid;
  @apply border-1;
  @apply border-gray-200;
  @apply text-xs;
  border-radius: 15px;
  outline: none;
  width: 150px;
  height: 30px;
}
.icon_search {
  @apply absolute;
  top: 8px;
  left: 14px;
  width: 13px;
  height: 13px;
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
.layout_icon {
  @apply ml-4;
}
</style>