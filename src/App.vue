<script setup>
import AlertComponent from './components/AlertComponent.vue';

const handleClose = () => {
    console.log('closed')
}

</script>
 
<template>
    <div class="flex flex-col p-5 space-y-4 w-[50%]">
        <AlertComponent type="info">
            New software update available.
        </AlertComponent>
        <AlertComponent type="success">
            Your purchase has been confirmed!
        </AlertComponent>
        <AlertComponent type="warning">
            Warning: Invalid email address!
        </AlertComponent>
        <AlertComponent type="error" @closed="handleClose">
            Error! Task failed successfully.
        </AlertComponent>
    </div>   
</template>