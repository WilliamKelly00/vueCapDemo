<template>
    <div>
        <h1>{{ msg }}</h1>
        <!-- create sign in, email password -->
        <h2> email </h2>
        <h2> password </h2>
        <button>Sign In</button>
        <button @click="Increment">{{ count }}</button>
    </div>
</template>

<script>
export default {
    name: 'SignIn',
    props: {
        msg: String,
    },
    data() {
        return {
            count: 0,
        }
    },
    methods: {
        Increment() {
            this.count++;
        }
    }
}
</script>

<style scoped>

</style>