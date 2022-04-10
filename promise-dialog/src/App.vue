<script setup lang="ts">
import { ref } from "vue";
import Dialog from "./components/Dialog.vue";

const refDialog=ref<null|InstanceType<typeof Dialog>>(null)
const onOpenDialogClick=async ()=>{
  const ok=await refDialog.value?.confirm()
  alert(ok?'OK':'キャンセル')

}
</script>

<template>
  <div style="background-color:white">

    <Dialog ref="refDialog" />

    <div >
      <button type="button" @click="onOpenDialogClick">ダイアログを開く</button>
    </div>
  </div>

</template>

