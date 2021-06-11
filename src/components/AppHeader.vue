<template>
    <div class="row header">
        <div class="container">
            <!--====Start Navigation=====-->
            <div class="navbar navbar-expand-lg navbar-dark">
                <a class="navbar-brand pl-5" href="#">Shopping</a>
                <button
                    class="navbar-toggler"
                    type="button"
                    data-toggle="collapse"
                    data-target="#navbarNav"
                    aria-control="nanbarNav"
                    aria-expanded="false"
                    aria-label="Toggle Navigation"
                >
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarNav">
                    <ul class="nav navbar-nav col-md-6">
                        <li class="nav-item px-3 active">
                            <router-link to="/recipes" exact>
                                <a class="nav-link">Recipes</a>
                            </router-link>
                        </li>
                        <li class="nav-item px-3">
                            <router-link to="/about">
                                <a class="nav-link">Shoping List</a>
                            </router-link>
                        </li>
                    </ul>
                    <ul class="nav navbar-nav navbar-right col-md-6">
                        <li class="nav-item px-3">
                            <router-link class="left" to="/login" replace>
                                <a class="nav-link">Logout</a>
                            </router-link>
                        </li>
                        <li class="nav-item px-3 dropdown">
                            <a
                                class="nav-link dropdown-toggle"
                                href="#"
                                id="navbarDropdownMenuLink"
                                data-toggle="dropdown"
                                aria-haspopup="true"
                                aria-expanded="false"
                            >
                                Manage
                            </a>
                            <div
                                class="dropdown-menu"
                                aria-labelledby="navbarDropdownMenuLink"
                            >
                                <a class="dropdown-item" href="#">Fetch Data</a>
                                <a class="dropdown-item" href="#">Save Data</a>
                            </div>
                        </li>
                    </ul>
                    <!-- <Dropdown style="margin-left:190px" class="drop" title="Manage" :items="Manage" />-->
                </div>
            </div>
            <!--====End Navigation=====-->
        </div>
    </div>
</template>
<script>
//import Dropdown from "./Dropdown";
export default {
    name: "AppHeader",
    components: {
        //  Dropdown,
    },
    data() {
        return {
            /*  Manage: [
        {
          title: "Fetch Data",
          link: "#",
        },
        {
          title: "Save Data",
          link: "#",
        },
      ],*/
        };
    }
};
</script>
<style lang="scss" scoped>
.header {
    background-color: rgb(59, 58, 58);

    border-radius: 5px;
    ul {
        float: left;
        width: calc(100%-200px);
        margin: 0;
        li {
            padding: 20px;
            display: inline-block;
            font-size: 18px;
            a {
                text-decoration: none;
            }
        }
    }
}
.dropdown-menu {
    background-color: rgb(59, 58, 58);
}
.dropdown-menu .dropdown-item {
    color: #fff;
    background-color: rgb(59, 58, 58);
}
</style>
