<template>


    <div>
        <p>
            {{ description }}

        </p>

    </div>

</template>

<script>
export default {
    name: 'HeaderComponent',
    props: {
        description: String,
    }
}
</script>

<style>
p{
    color: white;
}

</style>