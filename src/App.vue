
<template>
    <!-- Main -->
    <div class="App">
      <PortalHeader/>
      <div class="vertical-center portalBody">
         <div class="inner-block">
         <router-view> </router-view>
        </div>
      </div>
      <!-- <PortalFooter/> -->
    </div>
</template>

<script>

import PortalHeader from "@/components/portalHeader";
// import PortalFooter from "@/components/portalFooter";
export default {
  name: "App",
  components: {
   PortalHeader,
  //  PortalFooter
  },
};
</script>

