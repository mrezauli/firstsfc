<template>
    <!-- <div>
        <p>SlotComp.vue</p>
        <slot>
            <h4>This is fallback content</h4>
        </slot>
    </div> -->

    <h3>Component</h3>
    <div>
        <slot></slot>
    </div>
    <div>
        <slot></slot>
    </div>
</template>

<script></script>

<style scoped>
div {
    background-color: lightgreen;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
    flex-basis: 150px;
    border-radius: 10px;
    border: solid black 2px;
    margin: 10px;
    padding: 20px 10px 0 10px;
    height: 30px;
    width: 50%;
    font-weight: bold;
}

div:hover {
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
}

h4 {
    color: rgb(159, 0, 0);
}
</style>