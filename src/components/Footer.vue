<template>
  <div class="bg-nav_background">
    <div class="flex justify-center pt-12">
      <div class="flex justify-between container border-b-1 py-4">
        <div class="pr-10 justify-center">
          <div class="flex justify-center">
            <img src="../assets/images/footer_logo.png" class="footer_logo" alt=""/>
          </div>
          <p class="text-center text-rings_back_link_color my-4">
            We are dedicated to providing our customers with the highest quality diamond engagement rings and diamond jewellery.
          </p>
          <p class="text-center text-white">Follow Us</p>
          <div class="flex justify-center">
            <div class="footer_underline" />
          </div>
          <div class="flex justify-center my-8">
            <img src="../assets/images/facebook.png" class="mx-4" alt=""/>
            <img src="../assets/images/twitter.png" class="mx-4" alt=""/>
            <img src="../assets/images/instagram.png" class="mx-4" alt=""/>
            <img src="../assets/images/Pinterest.png" class="mx-4" alt=""/>
          </div>
        </div>
        <div
          v-for="(item, idx) in footer_data"
          :key="idx"
          class="mx-4"
          style="min-width:180px"
        >
          <div class="text-white text-md font-medium flex">{{ item.name }}</div>
          <div class="footer_underline" />
          <div
            v-for="(data, key) in item.data"
            :key="key"
            class=" text-rings_back_link_color text-sm my-2"
          >
            {{ data }}
          </div>
        </div>
      </div>
    </div>
    <div class="flex justify-center my-8">
      <div class="flex container justify-between">
        <div class="flex">
          <img src="../assets/images/img_group.png" class="footer_img py-2" alt=""/>
          <img src="../assets/images/google.png" class="footer_img" alt=""/>
          <img src="../assets/images/img_facebook.png" class="footer_img" alt=""/>
        </div>
        <div class="flex">
          <img src="../assets/images/visa.png" class="footer_img" alt=""/>
          <img src="../assets/images/MC.png" class="footer_img" alt=""/>
          <img src="../assets/images/AE.png" class="footer_img" alt=""/>
        </div>
      </div>
    </div>
     <div class="flex justify-center bg-top_bar_background py-4">
      <div class="flex container justify-between">
        <label class="text-rings_back_link_color">Copyright 2021 Steven Stone. All Rights Reserved.</label>
        <div class="flex text-rings_back_link_color">
          <label class="mx-4">Terms</label>
          <label class="mx-4">Privacy</label>
          <label class="mx-4">Compliance</label>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data: () => ({
    footer_data: [
      {
        name: 'Shop Online',
        data: ['Engagement Rings', 'Bridal', 'Jewellery', 'Collections', 'Bespoke', 'Loose Diamonds', 'Talk with an Expert']
      },
      {
        name: 'About Us',
        data: ['Our World', 'Why Shop Steven Stone', 'Our Showrooms', 'Our Bespoke Process', 'Our Conflict Free Promise', 'Giving Back', 'Our Blog']
      },
      {
        name: 'Customer Service',
        data: ['Contact Us', 'Store Locations', 'FAQs', 'Manufactoreres Warranty', 'Delievery Information', 'Shipping & Returns']
      },
      {
        name: 'Help & Guidance',
        data: ['Buying Guide', 'Diamond Guide', 'Finance Info', 'Wedding Guide']
      }
    ]
  })
}
</script>
<style scoped>
.footer_logo {
  text-align: center;
  width: 180px;
  height: 33px;
}
.footer_underline {
  @apply border-primary;
  @apply border-b-2;
  @apply my-2;
  width: 30px;
}
.footer_img {
  @apply mx-2;
  width: 57.5px;
  height: 26.5px;
}
</style>