<template>
    <div class="g-button-group">
        <slot></slot>
    </div>
</template>

<script>
    export default {
        name: "button-group",
        mounted() {
            let name = this.$el.children[0].nodeName.toLowerCase()
            if (name !== 'button') {
                console.warn(`g-button-group 组件子元素必须为 g-button , 你输入的是${name}, 需要更改，否则样式可能会出错`)
            }
        }
    }
</script>

<style lang="scss">
    .g-button-group {
        display: flex;

        > .g-button {
            border-radius: 0;
            &:not(:first-child) {
                margin-left: -1px;
            }
            &:hover {
                position: relative;
                z-index: 1;
            }
            &:first-child {
                border-top-left-radius: var(--border-radius);
                border-bottom-left-radius: var(--border-radius);
            }

            &:last-child {
                border-top-right-radius: var(--border-radius);
                border-bottom-right-radius: var(--border-radius);
            }
        }


    }
</style>