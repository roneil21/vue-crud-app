<template>
    <button>
        <slot>Create</slot>
    </button>
</template>

<script setup>

</script>

<style lang="scss" scoped>
button {
    padding: 8px 16px;
    border: none;
    cursor: pointer;

    &:hover {

        background-color: #F3CBAC;
    }
}
</style>