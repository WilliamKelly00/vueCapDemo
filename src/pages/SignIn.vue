<template>
    <div>
        <h1>Sign In!</h1>
        <!-- create sign in, email password -->
        <label>Email:</label>
        <input v-model="email" type="text" />
        <label>Password:</label>
        <input v-model="password" type="password" />
        <button>Sign In</button>
        <button>Sign Up</button>

        <div>
            <button>Sign In with Google</button>
            <button>Sign In with Facebook</button>
        </div>
    </div>
</template>

