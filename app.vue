<script setup lang="ts">

</script>

<template>
  <div class="area">
    <div class="head">
      <TheHeader></TheHeader>
    <ActiveZone></ActiveZone>
    </div>
    <ExcursionZone></ExcursionZone>
    <TurInf></TurInf>
    <EventsZone></EventsZone>
    <TravelGuide></TravelGuide>
  </div>
  <!-- <TabAndcroll></TabAndcroll> -->
</template>

<style scoped>
.area{
  padding: 62px 20px 0px 20px;
  display: flex;
  flex-direction: column;
  gap: 64px;
}
.head{
  display: flex;
  flex-direction: column;
  gap: 16px;
}
</style>
<script lang="ts">
import { EventsDatePicker } from '#components';
import TabAndcroll from './components/TabAndcroll.vue';





</script>