<template>
    <div>
        <h1>Sign In!</h1>
        <!-- create sign in, email password -->
        <label>Email:</label>
        <input v-model="email" type="text" />
        <label>Password:</label>
        <input v-model="password" type="password" />
        <button>Sign Up</button>
        <button>Sign In</button>

        <div>
            <button>Sign Up with Google</button>
            <button>Sign Up with Facebook</button>
        </div>
    </div>
</template>

