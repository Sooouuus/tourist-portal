<script setup lang="ts">
import { TabsContent, TabsIndicator, TabsList, TabsRoot, TabsTrigger, ScrollAreaScrollbar, ScrollAreaViewport, ScrollAreaRoot  } from 'reka-ui'
</script>
<template>
    <div class="container">
        <TabsRoot
    class="TabsRoot"
    default-value="tab1"
  >
    <TabsList
      class="TabsList"
    >
      <TabsIndicator class="TabsIndicator">
        <div
          style="width: 100%; height: 100%"
          class="bg-grass8 w-full h-full"
        ></div>
      </TabsIndicator>

      <div style="display: flex;">
      <TabsTrigger
        class="tabs"
        value="tab1"
      >
        Музеи
      </TabsTrigger>
      <TabsTrigger
        class="tabs"
        value="tab2"
      >
        Улицы
      </TabsTrigger>
      <TabsTrigger
        class="tabs"
        value="tab3"
      >
        Набережные
      </TabsTrigger>
      <TabsTrigger
        class="tabs"
        value="tab4"
      >
        Смотровые площадки
      </TabsTrigger>
      <TabsTrigger
        class="tabs"
        value="tab5"
      >
        Театры
      </TabsTrigger>
       <TabsTrigger
        class="tabs"
        value="tab6"
      >
        Сады
      </TabsTrigger>
      </div>
      <TabsContent
      class="TabsContent"
      value="tab1"
    >
      <Ex name="hhh1"  value="tab1"/>
      </TabsContent>
      <TabsContent
      class="TabsContent"
      value="tab2"   >
      <Ex name="hhh2"  value="tab2"/>
      </TabsContent>
      <TabsContent
      class="TabsContent"
      value="tab3"
    >
      <Ex name="hhh3"  value="tab3"/>
      </TabsContent>
      <TabsContent
      class="TabsContent"
      value="tab4"
    >
      <Ex name="hhh4"  value="tab4"/>
      </TabsContent>
      <TabsContent
      class="TabsContent"
      value="tab5"
    >
      <Ex name="hhh5"  value="tab5"/>
      </TabsContent>
      <TabsContent
      class="TabsContent"
      value="tab6"
    >
      <Ex name="hhh6"  value="tab6"/>
      </TabsContent>

    </TabsList>
</TabsRoot>
<ScrollAreaRoot
    class="ScrollAreaRoot"
    style="--scrollbar-size: 10px"
  />
<ScrollAreaViewport class="ScrollAreaViewport">
      <div :style="{ padding: '15px 20px' }">
        <div class="Text">
          Достопримечательности
        </div>
        <div
          v-for="tag in TabsTrigger"
          :key="tag"
          class="Tag"
        >
          {{ tag }}
        </div>
      </div>
    </ScrollAreaViewport>
      <ScrollAreaScrollbar
      class="ScrollAreaScrollbar"
      orientation="vertical"
    />
    </div>
</template>
<style scoped>
.tabs{
    display: flex;
    flex-direction: row;
    gap: 16px;
    font-family: 'Grotesk';
}
.conteiner{
    display: flex;
    flex-direction: column;
}

.TabsContent {
  flex-grow: 1;
  padding: 20px;
  background-color: white;
  border-bottom-left-radius: 6px;
  border-bottom-right-radius: 6px;
  outline: none;
}
.TabsRoot {
  display: flex;
  flex-direction: column;
  width: 300px;
  box-shadow: 0 2px 10px var(--black-a4);
}

.TabsList {
  flex-shrink: 0;
  /* display: flex; */
  /* flex-direction: row; */
  border-bottom: 1px solid var(--mauve-6);
  position: relative;
}
.TabsIndicator {
  position: absolute;
  padding-left: 2rem;
  left: 0;
  height: 2px;
  bottom: 0;
  width: var(--reka-tabs-indicator-size);
  transform: translateX(var(--reka-tabs-indicator-position));
  border-radius: 9999px;
  transition-property: width, transform;
  transition-duration: 300ms;
}
.TabsTrigger {

  background-color: black;
  padding: 0 20px;
  height: 45px;
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 15px;
  line-height: 1;
  color: var(--mauve-11);
  user-select: none;
  }
  .Fieldset {
  margin-bottom: 15px;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}
</style>