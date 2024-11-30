<template>
    <div class="container">

        <div v-for="field in fields" :key="field.title">
            <h1 @click="$emit('section-click', field.title)">{{ field.title }}</h1>
        </div>

        <div v-for="icon in icons" :key="icon.title">
            <h1>
                <img :src="icon.imageUrl" alt="test" class="iconLink">
            </h1>
        </div>
    </div>
</template>
<script>
export default {
    name: 'HeaderComponent',
    props: {
        fields: Array,
        icons: Array
    }
}
</script>
<style scoped>
.container {
    display: flex;
    flex-direction: row;
    background-color: #1B1B1B;
    justify-content: space-around;
    border-radius: 10px;

}

.container h1 {
    color: #9C9C9C;
    font-size: 14px;
}

.container h1:hover {
    color: #FFFFFF;
    font-size: 14px;
}
.container img{
    width: 20px;
    height: 20px;
}
.iconLink{
    /* Remove the background of the image */
    background-color: transparent;
}
</style>