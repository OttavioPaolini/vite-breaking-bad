<script>
export default {
    name: "AppCard",
    props: {
        character: Object
    }
}
</script>


<template>
    <div class="my_cards">
        <img :src="character.img" :alt="character.name">
        <h2>{{character.name}}</h2>
        <h3>{{character.category}}</h3>
        <h4>{{character.status}}</h4>
    </div>
</template>


<style lang="scss" scoped>
@use "./style/partials/variables" as *;
.my_cards{
    height: 500px;
    padding: 1.5rem;
    margin-top: 1rem;
    background-color: $bg-color;
    text-align: center;
    h2{
        color: $primary-font-color;

    }
    h3{
        color: $second-font-color;
    }
    h4{
        color: $third-font-color;
    }
}

</style>