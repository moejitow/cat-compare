<template>
    <header>
        <div id="logo">
            <img v-if="image" alt="Vue logo" :src="require(`@/assets/${image}`)">
             <h1>{{ title }}</h1>
        </div>
        <div id="nav">
            <router-link to="/"><h2>Home</h2></router-link>
            <router-link to="/about"><h2>About</h2></router-link>
            <!-- <h2 class="link" v-for="page in pages" :key=page>{{ page }}</h2> -->
        </div>
    </header>
</template>

<script>
export default {
    name: "Header",
    props: {
        image: {
            required: false,
            type: String
        },
        title: {
            required: true,
            type: String
        },
        pages: {
            required: true,
            type: Array
        }
    },
}
</script>

<style scoped>
header {
    background: #669DB3FF;
    color: #DFDCE5FF;

    max-height: 6vw;
    height: auto;

    display: flex;
    align-items: center;

    justify-content: space-between;
}

#logo {
    display: flex;
    align-items: center;
}

img {
    max-height: 6vw;
    height: auto;
}

h1 {
    font-size: 3vw;
    padding-left: 1vw;
}
#nav {
    display: flex;
    align-items: center;
}

#nav a {
    padding-right: 60px;
    color: #DFDCE5FF;
  font-weight: bold;
    font-size: 1.5rem;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>