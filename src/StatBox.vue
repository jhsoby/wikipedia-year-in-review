<template>
<div class="statbox">
    <cdx-icon :icon="icon"></cdx-icon>
    <span class="statbox-label" v-html="impactMessage"></span>
</div>
</template>
<script>
import { CdxIcon } from '@wikimedia/codex';
import message from './message';
export default {
    name: 'StatBox',
    components: {
        CdxIcon
    },
    computed: {
        impactMessage() {
            let valString = message.convertNumber( this.value );
            return message.impactMessage( this.message, valString );
        }
    },
    props: {
        icon: String|Object,
        value: {
            type: Number,
        },
        message: {
            type: String
        }
    }
};
</script>
<style>
.statbox {
    width: 90px;
    background: white;
    padding: 8px;
    color: #333;
    border-radius: 5px;
    padding-left: 40px;
    position: relative;
}
.statbox span {
    display: block;
    text-align: left;
}
span.statbox-label {
    display: flex;
    flex-direction: column;
    font-size: 0.75rem;
}
.statbox-label .highlight {
    font-size: 1.25rem;
    font-weight: 700;
}
.statbox .cdx-icon {
    position: absolute;
    left: 8px;
    top: 8px;
    botton: 8px;
}
</style>