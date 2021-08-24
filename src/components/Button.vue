<template>
    <button @click="onClick()" class="btn" :style=" { background: color } ">{{title}}</button>
</template>

<script>
    export default {
        name : 'Button',
        props: {
            title: {
                type: String,
                default: 'Add task',
            },
            color: {
                type: String,
            } 
        },

        methods: {
            onClick() {
                console.log("click");
            }
        }
    }
</script>
