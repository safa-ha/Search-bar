
<script setup>
const props = defineProps({
    info: {
        type: Object,
        required: true
    }
})
</script>

<template>
    <div>
        {{ props.info.name }} <br />
        {{ props.info.address }}, {{ props.info.postalZip }}, {{ props.info.region }} <br />
        {{ props.info.phone }} <br />
        {{ props.info.email }}
    </div> <br />
</template>