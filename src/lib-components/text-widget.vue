<template>
    <v-text-field :label="label"></v-text-field>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
    name: "TextWidget",
    props: {
        value: {
            type: String,
            default: null,
        },
        label: {
            type: String,
            required: true,
        },
        description: {
            type: String,
            default: null,
        },
        readonly: {
            type: Boolean,
            default: false,
        },
        disabled: {
            type: Boolean,
            default: false,
        },
    },
    data() {},
});
</script>
