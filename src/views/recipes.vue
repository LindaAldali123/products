<template>
    <div class="home">
        <app-header />
        <div class="row">
            <button class="btn btn-primary">New Recipe</button>
            <br />
            <h1>Please Select a Recipe!</h1>
        </div>
        <products />
    </div>
</template>

<script>
// @ is an alias to /src
import products from "@/components/products.vue";
import AppHeader from "@/components/AppHeader.vue";
//import prices from "../json/prices.json";
export default {
    name: "recipes",
    components: {
        products,
        AppHeader
    }
};
</script>
<style scoped>
.home button {
    margin-top: 20px;
    padding: 15px 15px;
    margin-left: 50px;
    font-weight: bold;
    color: cornsilk;
    font-size: 16px;
    float: left;
    background-color: #42b983;
    border-radius: 5px;
    height: 60px;
    width: 180px;
}
.home .row h1 {
    margin-bottom: 60px;
    text-align: center;
    margin-left: 380px;
    margin-top: 75px;
    color: darkcyan;
}
@media (max-width: 767px) {
    .home .row h1 {
        margin-bottom: 60px;
        text-align: center;
        margin-left: 20px !important;
        margin-top: 75px;
        color: darkcyan;
    }
}
</style>
