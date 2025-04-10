<script setup lang="ts">
const props = defineProps<{

}>()
</script>
<template>
    <div class="events-area">
        <h1>События</h1>
        <div class="events-inf-area">
            <!-- <BlockZ class="date-choose-area">
                <TextBaseText base-text="Месяц" class="month-choose-text"></TextBaseText>
                <div style="height: 30px; background-color: aqua;">dates</div>
            </BlockZ>
                
            <div class="events-list">
                <Ex name="09 фпреля"></Ex>
                <Ex name="09 фпреля"></Ex>
                <Ex name="09 фпреля"></Ex>
            </div> -->
            <CaledarFr></CaledarFr>
        </div>
    </div>
</template>

<style scoped>
.events-area{
    display: flex;
    flex-direction: column;
    gap: 16px;
}
.events-inf-area{
    display: grid;
    grid-template-rows: 1fr 2fr;
    grid-template-columns: 1fr;
    gap: 16px;
}
.date-choose-area{
    padding: 10px 16px;
}
.month-choose-text{
    color: #797979;
    font-size: 10px;
}
.events-list{
    display: flex;
    flex-direction: row;
    gap: 16px;
}
</style>