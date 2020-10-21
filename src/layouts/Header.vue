<template>
    <header>
        <div id="logo">
            <img v-if="image" alt="Vue logo" :src="require(`@/assets/${image}`)">
             <h1>{{ title }}</h1>
        </div>
        <div id="nav">
            <h2 class="link" v-for="page in pages" :key=page>{{ page }}</h2>
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
#nav {
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
.link {
    padding-right: 2vw;
}
</style>