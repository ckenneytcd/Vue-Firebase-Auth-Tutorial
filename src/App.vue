<template>
    <div id="app">
        <div id="nav">
            <router-link to="/Login">Login</router-link> |
            <router-link to="/register">Register</router-link> |
            <router-link to="/">Home</router-link> |
            <button @click="logout">Logout</button>
        </div>
        <router-view />
    </div>
</template>

<script>
import firebase from 'firebase';

export default {
    methods: {
        logout() {
            firebase
                .auth()
                .signOut()
                .then(() => {
                    alert('Successfully logged out');
                    this.$router.push('/');
                })
                .catch(error => {
                    alert(error.message);
                    this.$router.push('/');
                });
        },
    },
};
</script>
<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}

#nav {
    padding: 30px;
}

#nav a {
    font-weight: bold;
    color: #2c3e50;
}

#nav a.router-link-exact-active {
    color: #42b983;
}

input {
    margin-right: 20px;
}
</style>
