<template>
    <div class="wave-forms-sample">
        <p>
            The counter was {{ changedBy }} to <b>{{ counter }}</b
            >.
        </p>
        <text-widget label="cf?" v-model="data.text1" />
    </div>

    <div></div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

interface SampleData {
    counter: number;
    initCounter: number;
    message: {
        action: string | null;
        amount: number | null;
    };
    data: {
        text1: string | null;
    };
}

export default /*#__PURE__*/ defineComponent({
    name: "WaveFormsSample", // vue component name
    components: {
        TextWidget: () => import("./text-widget.vue"),
    },
    data(): SampleData {
        return {
            counter: 5,
            initCounter: 5,
            message: {
                action: null,
                amount: null,
            },
            data: {
                text1: null,
            },
        };
    },
    computed: {
        changedBy() {
            const { message } = this as SampleData;
            if (!message.action) return "initialized";
            return `${message.action} ${message.amount || ""}`.trim();
        },
    },
    methods: {
        increment(arg: Event | number): void {
            const amount = typeof arg !== "number" ? 1 : arg;
            this.counter += amount;
            this.message.action = "incremented by";
            this.message.amount = amount;
        },
        decrement(arg: Event | number): void {
            const amount = typeof arg !== "number" ? 1 : arg;
            this.counter -= amount;
            this.message.action = "decremented by";
            this.message.amount = amount;
        },
        reset(): void {
            this.counter = this.initCounter;
            this.message.action = "reset";
            this.message.amount = null;
        },
    },
});
</script>

<style scoped>
.wave-forms-sample {
    display: block;
    width: 400px;
    margin: 25px auto;
    border: 1px solid #ccc;
    background: #eaeaea;
    text-align: center;
    padding: 25px;
}
.wave-forms-sample p {
    margin: 0 0 1em;
}
</style>
