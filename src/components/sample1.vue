<template>
    <div class="container">
        <div class="box">
            
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {};
    },
    mounted() {},
    computed: {},
    methods: {}
}
</script>

<style>
.container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh; 
    background-color: lightgray;
}

.box {
    width: 80%; 
    max-width: 500px; 
    height: 70%; 
    max-height: 700px; 
    background-color: green; 
    box-sizing: border-box; 
}

@media (max-width: 600px) {
    .box {
        height: 80%; 
    }
}
</style>
