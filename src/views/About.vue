<template>
    <div class="shoplist">
        <app-header />
        <shoplist />
    </div>
</template>
<script>
// @ is an alias to /src
import shoplist from "@/components/shoplist.vue";
import AppHeader from "@/components/AppHeader.vue";

export default {
    name: "About",
    components: {
        shoplist,
        AppHeader
    }
};
</script>
