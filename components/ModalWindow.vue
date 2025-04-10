<script setup lang="ts">
import {
  AlertDialogAction,
  AlertDialogCancel,
  AlertDialogContent,
  AlertDialogDescription,
  AlertDialogOverlay,
  AlertDialogPortal,
  AlertDialogRoot,
  AlertDialogTitle,
  AlertDialogTrigger,
} from 'reka-ui'


function handleAction() {
  alert('clicked action button!')
}
</script>

<template>
  <AlertDialogRoot>
    <AlertDialogTrigger class="ButtonRed">
      Перейти
    </AlertDialogTrigger>
    <AlertDialogPortal>
      <AlertDialogOverlay class="AlertDialogOverlay" />
      <AlertDialogContent class="AlertDialogContent">
        <AlertDialogTitle class="AlertDialogTitle">
          Игра еще в разработке
        </AlertDialogTitle>
        <div :style="{ display: 'flex', gap: 25, justifyContent: 'flex-end' }">
          <AlertDialogCancel class="Button mauve">
            Я тебя прощаю
          </AlertDialogCancel>
        </div>
      </AlertDialogContent>
    </AlertDialogPortal>
  </AlertDialogRoot>
</template>
<style>



.AlertDialogOverlay {
  background-color: var(--black-a9);
  position: fixed;
  inset: 0;
  animation: overlayShow 150ms cubic-bezier(0.16, 1, 0.3, 1);
}
.ButtonRed{
    padding: 5px 25px;
    width: fit-content;
    display: flex;
    border: none;
    border-radius: 20px;
    color: #FFFFFF;
    background-color: #E90729;
    display: inline-flex;
    justify-content: center;
}
.AlertDialogContent {
  background-color: white;
  border-color: black;
  border-radius: 6px;
  box-shadow: hsl(206 22% 7% / 35%) 0px 10px 38px -10px, hsl(206 22% 7% / 20%) 0px 10px 20px -15px;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 90vw;
  max-width: 500px;
  max-height: 85vh;
  padding: 25px;
  animation: contentShow 150ms cubic-bezier(0.16, 1, 0.3, 1);
}

.AlertDialogTitle {
  margin: 0;
  color: var(--mauve-12);
  font-size: 17px;
  font-weight: 500;
}


</style>