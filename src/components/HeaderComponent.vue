<template>
    <div class="container" v-for="field in fields" :key="field.title">
        <h1 v-if="!field.externalContent">{{ field.title }}</h1>
        
        <h1 v-else >
            <img :src="field.imageUrl" alt="test">
            <!-- <a :href="field.imageUrl" target="_blank">teste</a> -->
        </h1>
    </div>
</template>
<script>
export default {
    name: 'HeaderComponent',
    props: {
        fields: Array
    }
}
</script>
<style scoped>
.container {
    display: flex;
    justify-content: space-between;
    flex-direction: row;
    background-color: #1B1B1B;
}

.container h1 {
    color: #9C9C9C;
    font-size: 14px;
}

.container h1:hover {
    color: #FFFFFF;
    font-size: 14px;
}
</style>