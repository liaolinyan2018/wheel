<template>
    <div>
        <button class="g-button" :class="{[`icon-${iconPosition}`]: true}">
            <g-icon name="loading" class="loading icon" v-if="loading"></g-icon>
            <g-icon :name="icon" class="icon" v-if="icon && !loading"></g-icon>
            <div class="text">
                <slot></slot>
            </div>
        </button>
    </div>
</template>

<script>
    import GIcon from "./icon";

    export default {
        name: "g-button",
        components: {GIcon},
        // props: ['icon', 'iconPosition']
        props: {
            icon: {},
            loading: {
                type: Boolean,
                default: false
            },
            iconPosition: {
                type: String,
                default: 'left',
                validator(value) {
                    return value === 'left' || value === 'right'
                }
            }
        }
    }
</script>

<style lang="scss">
    @keyframes spin {
        0% {
            transform: rotate(0deg);
        }
        100% {
            transform: rotate(360deg);
        }
    };

    .g-button {
        height: var(--button-height);
        padding: 0 1em;
        font: inherit;
        border-radius: var(--border-radius);
        border: 1px solid var(--border-color);
        background: var(--button-bg);
        display: inline-flex;
        justify-content: center;
        align-items: center;

        &:hover {
            border-color: var(--border-color-hover);
        }

        &:active {
            background: var(--button-active-bg);
        }

        &:focus {
            outline: none;
        }

        > .icon {
            width: 1em;
            height: 1em;
            fill: currentColor;
            overflow: hidden;
            order: 1;

        }

        > .text {
            order: 2;
            line-height: 1em;
            margin-left: .1em;
            margin-right: 0;
        }

        &.icon-right {
            > .text {
                order: 1;
                margin-right: .1em;
                margin-left: 0;
            }

            > .icon {
                order: 2;
            }
        }

        .loading {
            animation: spin 2s infinite linear;
        }
    }
</style>