<script lang="ts" setup>
import { reactive,ref } from "@vue/reactivity"

const show=ref(false)

const promiseInfo=reactive({
    resolve:null as null|((v:any)=>void)
})

function confirm():Promise<boolean>{
    return new Promise((resolve)=>{
        promiseInfo.resolve=resolve;
        show.value=true
    })
}

defineExpose({
    confirm
})

const onOkClick=()=>{
    show.value=false;
    promiseInfo.resolve?.(true);
}

const onCancelClick=()=>{
    show.value=false;
    promiseInfo.resolve?.(false);
}
</script>

<template>
    <div style="width:100vw;height:100vh;position: fixed;top:0px;left:0px;display:flex; justify-content: center;align-items: center;background-color: bisque;';" v-if="show">
        <div>
            <h1>ダイアログ</h1>

            <div>
                <button type="button" @click="onOkClick">OK</button>
                <button type="button" @click="onCancelClick">キャンセル</button>
            </div>
        </div>

    </div>
</template>