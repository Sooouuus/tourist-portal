<script setup lang="ts">
import { TabsContent, TabsIndicator, TabsList, TabsRoot, TabsTrigger } from 'reka-ui'
</script>
<template>
    <div>
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
      <TabsTrigger
        class="TabsTrigger"
        value="tab1"
      >
        Account
      </TabsTrigger>
      <TabsTrigger
        class="TabsTrigger"
        value="tab2"
      >
        Password
      </TabsTrigger>
    </TabsList>
</TabsRoot>
    </div>
</template>