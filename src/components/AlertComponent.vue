<script setup>
import { computed, ref } from 'vue';
import IconInfo from './icons/IconInfo.vue';
import IconError from './icons/IconError.vue';
import IconSuccess from './icons/IconSuccess.vue';
import IconWarning from './icons/IconWarning.vue';
const props = defineProps({
    type: {
        type: String,
        default: 'info'
    }
})

const emit = defineEmits(['closed'])


const alertType = computed(() => {
    return {
        info: 'alert-info',
        warning: 'alert-warning',
        error: 'alert-error',
        success: 'alert-success'
    }[props.type]
})

const iconType = computed(() => {
    return {
        info: IconInfo,
        warning: IconWarning,
        error: IconError,
        success: IconSuccess
    }[props.type]
})

const closed = ref(false)

const close = () => {
    closed.value = true
    emit('closed')
}

</script>

<template>
    <div v-if="!closed" role="alert" :class="`alert ${alertType}`">
        <component :is="iconType"></component>
        <span><slot></slot></span>
        <button @click="close">X</button>
    </div>
</template>