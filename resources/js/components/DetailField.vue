<template>
    <PanelItem :index="index" :field="field"/>
</template>

<script>
export default {
    props: ['resource', 'resourceName', 'resourceId', 'field'],
    created() {
        if (Array.isArray(this.field.value)) {
            this.field.value = this.field.value.join(", ");
        }
    },
}
</script>
