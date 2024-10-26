<script>
   
    export default {
        props: {
        title: String,
        body: String
    },

    setup(props) {
        
    }
    }
</script>

<template>
    <div>
        <h1>{{title}}</h1>
        <p>{{body}}</p>
    </div>
</template>