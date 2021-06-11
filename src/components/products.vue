<template>
    <div class="products">
        <div
            data-aos="fade-up"
            class=" row"
            v-for="product in products"
            v-bind:key="product.id"
        >
            <div
                class="lin col-md-4"
                @click.prevent="
                    product.klic = !product.klic;
                    hide = !hide;
                "
                :class="[product.klic === true ? 'act' : ' ']"
            >
                <div class="col-md-3">
                    <h2>{{ product.title }}</h2>
                    <h6>{{ product.description }}</h6>
                </div>
                <div class="col-md-7"></div>
                <div class="img col-md-2">
                    <img v-bind:src="product.img" />
                </div>
            </div>
            <div class="col-md-2"></div>
            <transition class="trans col-md-6" name="fade" appear>
                <div
                    class="info"
                    style="border:1px solid #DDD "
                    @click.stop="product.klic"
                    v-if="product.klic && hide"
                    v-bind:key="product.id"
                    :class="[product.klic === true ? 'active' : ' ']"
                >
                    <!--Add Hide -->
                    <img
                        v-bind:src="product.img"
                        style="width:520px;height:270px;"
                    />
                    <h2 style="margin-right:360px;margin-bottom:0px">
                        {{ product.title }}
                    </h2>
                    <Dropdown2
                        style="margin-right:340px;padding:10px;font-size:15px;margin-bottom:0px"
                        class="drop"
                        title="Manage Recipe"
                        :items="Manage"
                    />
                    <button
                        @click.prevent="
                            edit = !edit;
                            hide = !hide;
                        "
                        style="margin:3px;padding:5;background-color:rgb(98, 132, 184);color:#FFF;border:1px solid rgb(98, 132, 184);"
                    >
                        Edit Recipe
                    </button>
                    <!--Add Hide -->
                    <button
                        @click.stop="
                            del(product.id);
                            product.klic = !product.klic;
                            hide = !hide;
                        "
                        style="margin:3px;padding:5;background-color:red;color:#FFF;border:1px solid red;"
                    >
                        Delete Recipe
                    </button>
                    <h4 style="margin-right:380px">
                        {{ product.description }}
                    </h4>
                    <h6
                        class="col-md-6"
                        style="margin-right:350px;margin-left:10px;"
                    >
                        {{ product.tit }} ({{ product.nu1 }})
                    </h6>
                    <h6
                        class="col-md-6"
                        style="margin-right:350px;margin-left:10px;"
                    >
                        {{ product.tit2 }} ({{ product.nu2 }})
                    </h6>
                </div>
            </transition>
            <transition class="trans" name="fade" appear>
                <div
                    class="info2"
                    @click.stop="edit"
                    v-if="product.klic && edit"
                    style="margin-left:680px;border:1px solid #DDD "
                    v-bind:key="product.id"
                    :class="[product.klic === true ? 'activ' : ' ']"
                >
                    <button
                        style="background-color:green;color:#FFF;padding:5px;"
                        @click.stop="save"
                    >
                        Save
                    </button>
                    <button
                        style="background-color:red; margin:8px;color:#FFF;padding:5px;"
                        @click.prevent="
                            edit = !edit;
                            hide = !hide;
                        "
                    >
                        <!--Hide-->
                        Cancel
                    </button>
                    <button
                        style="background-color:blue;color:#FFF;padding:5px;"
                        @click.stop="
                            product.tit = '';
                            product.tit2 = '';
                            product.nu1 = '';
                            product.nu2 = '';
                        "
                    >
                        <!--product.title='';product.description='';product.img='';-->
                        Clear
                    </button>
                    <br />Name :
                    <input
                        type="product"
                        v-bind:value="product.title"
                        style="width:400px; height:30px; margin-bottom:10px"
                    />
                    <br />Image URL :
                    <input
                        type="product"
                        v-bind:value="product.img"
                        style="width:400px; height:30px; margin-bottom:10px"
                    />
                    <br />
                    <img
                        v-bind:src="product.img"
                        style="width:540px;height:270px;"
                    />
                    <p style="font-weight:bold;font-size:19px;">Description:</p>
                    <input
                        type="product"
                        v-bind:value="product.description"
                        style="width:400px; height:90px; margin-bottom:10px"
                    />
                    <div class="pr">
                        <input
                            type="product"
                            v-bind:value="product.tit"
                            style="width:200px; height:30px; margin-bottom:10px;margin:2px;"
                        />
                        <input
                            type="product"
                            v-bind:value="product.nu1"
                            style="width:200px; height:30px; margin-bottom:10px;margin:2px;"
                        />
                    </div>
                    <div class="pr2">
                        <input
                            type="product"
                            v-bind:value="product.tit2"
                            style="width:200px; height:30px; margin-bottom:10px;margin:2px;"
                        />
                        <input
                            type="product"
                            v-bind:value="product.nu2"
                            style="width:200px; height:30px; margin-bottom:10px;margin:2px;"
                        />
                        <form action="">
                            <div
                                class="lis  row"
                                v-for="ou in outp"
                                v-bind:key="ou.done"
                            >
                                <h5
                                    style="border:1px solid black;margin-left:85px;width:200px"
                                >
                                    {{ ou.wor }}
                                </h5>
                                <h5 style="border:1px solid black;width:190px">
                                    {{ ou.wow }}
                                </h5>
                                <button
                                    @click.stop="delet(index)"
                                    style="height:25px !important;background-color:red;color:#FFF;padding:2px;margin:2px;"
                                >
                                    delete
                                </button>
                            </div>
                            <input
                                type="product"
                                v-model="inpu1"
                                style="width:160px; height:30px; margin-bottom:10px;margin:2px;"
                            />
                            <input
                                type="product"
                                v-model="inpu2"
                                style="width:160px; height:30px; margin-bottom:10px;margin:2px;"
                            />
                            <div
                                class="row"
                                style="margin-left:60px;margin:8px"
                            >
                                <button
                                    style="background-color:green;color:#FFF;padding:8px;"
                                    @click.prevent="Add"
                                    :disabled="!inpu1 && !inpu2"
                                >
                                    Add Ingradian
                                </button>
                            </div>
                        </form>
                    </div>
                </div>
            </transition>
        </div>
    </div>
</template>

<script>
require(["aos"], function(AOS) {
    AOS.init({
        easing: "ease-in-out-sine"
    });
});
import Dropdown2 from "./Dropdown2";
export default {
    name: "products",
    components: {
        Dropdown2
    },
    data: function() {
        return {
            products: [
                {
                    id: 0,
                    title: "cake",
                    description: "Syrian cake",
                    img: require("../assets/cake.jpg"),
                    tit: "sugher ",
                    tit2: "eggs",
                    nu1: 2,
                    nu2: 3,
                    klic: false
                },
                {
                    id: 1,
                    title: "meat",
                    description: "Syrian meat",
                    img: require("../assets/meat.jpg"),
                    tit: "proteen ",
                    tit2: "chiken",
                    nu1: 2,
                    nu2: 3,
                    klic: false
                },
                {
                    id: 2,
                    title: "pizaa",
                    description: "Syrian pizaa",
                    img: require("../assets/pizaa.jpg"),
                    tit: "tomato ",
                    tit2: "salt",
                    nu1: 2,
                    nu2: 1,
                    klic: false
                },
                {
                    id: 3,
                    title: "vegitable",
                    description: "Syrian vegitable",
                    img: require("../assets/vege.jpg"),
                    tit: "appel",
                    tit2: "bananas",
                    nu1: 4,
                    nu2: 3,
                    klic: false
                },
                {
                    id: 4,
                    title: "cake",
                    description: "Syrian cake",
                    img: require("../assets/cake.jpg"),
                    tit: "sugher",
                    tit2: "eggs",
                    nu1: 2,
                    nu2: 3,
                    klic: false
                },
                {
                    id: 5,
                    title: "meat",
                    description: "Syrian meat",
                    img: require("../assets/meat.jpg"),
                    tit: "proteen ",
                    tit2: "chiken",
                    nu1: 2,
                    nu2: 3,
                    klic: false
                },
                {
                    id: 6,
                    title: "pizaa",
                    description: "Syrian pizaa",
                    img: require("../assets/pizaa.jpg"),
                    tit: "tomato ",
                    tit2: "salt",
                    nu1: 2,
                    nu2: 3,
                    klic: false
                },
                {
                    id: 7,
                    title: "vegitable",
                    description: "Syrian vegitable",
                    img: require("../assets/veg.jpg"),
                    tit: "appel",
                    tit2: "bananas",
                    nu1: 2,
                    nu2: 3,
                    klic: false
                },
                {
                    id: 8,
                    title: "Cake",
                    description: "Syrian Cake",
                    img: require("../assets/cak.jpg"),
                    tit: "crema",
                    tit2: "chockolate",
                    nu1: 3,
                    nu2: 4,
                    klic: false
                },
                {
                    id: 9,
                    title: "Cake",
                    description: "Syrian Cake",
                    img: require("../assets/cakk.jpg"),
                    tit: "crema",
                    tit2: "chockolate",
                    nu1: 3,
                    nu2: 4,
                    klic: false
                },
                {
                    id: 10,
                    title: "nuts",
                    description: "Syrian nuts",
                    img: require("../assets/loz.jpg"),
                    tit: "crema",
                    tit2: "nuts",
                    nu1: 3,
                    nu2: 4,
                    klic: false
                },
                {
                    id: 11,
                    title: "Cake",
                    description: "Syrian Cake",
                    img: require("../assets/stro.jpg"),
                    tit: "crema",
                    tit2: "chockolate",
                    nu1: 3,
                    nu2: 4,
                    klic: false
                },
                {
                    id: 12,
                    title: "Humbrger",
                    description: "Syrian Humbrger",
                    img: require("../assets/hum.jpg"),
                    tit: "meat",
                    tit2: "bread",
                    nu1: 2,
                    nu2: 3,
                    klic: false
                },
                {
                    id: 13,
                    title: "Fruit",
                    description: "Syrian Fruit",
                    img: require("../assets/frui.jpg"),
                    tit: "banana",
                    tit2: "orange",
                    nu1: 2,
                    nu2: 3,
                    klic: false
                },
                {
                    id: 14,
                    title: "drink",
                    description: "Syrian drink",
                    img: require("../assets/lem.jpg"),
                    tit: "lemon",
                    tit2: "water",
                    nu1: 2,
                    nu2: 3,
                    klic: false
                }
            ],
            Manage: [
                {
                    title: "To Shopping List",
                    link: "/about"
                },
                {
                    title: "Edit Recipe",
                    link: "#"
                },
                {
                    title: "Delete Recipe",
                    link: "#"
                }
            ],
            emp: {
                inp1: " ",
                inp2: " ",
                inp3: " ",
                inp4: " ",
                inp5: " "
            },
            inpu1: " ",
            inpu2: " ",
            outp: [],
            edit: false,
            hide: false
        };
    },
    methods: {
        del(index1) {
            this.products.splice(index1, 1);
        },
        Add() {
            this.outp.push({ wor: this.inpu1, wow: this.inpu2, done: false });
            this.inpu1 = "";
            this.inpu2 = "";
        },
        delet(index) {
            this.outp.splice(index, 1);
        },
        save() {
            this.products.push({
                title: this.product.title,
                description: this.product.description,
                img: this.product.img,
                tit: this.product.tit,
                tit2: this.product.tit2,
                nu1: this.product.nu1,
                nu2: this.product.nu2,
                klic: false
            });
        }
    }
};
</script>
<style scoped>
.products {
    margin-left: 36px !important;
}

.img img {
    float: left;
    width: 130px !important;
    height: 90px;
    padding: 3px;
    margin-top: -88px;
    margin-left: 282px;
    margin-bottom: 2px;
}
.lin {
    border: 1px solid rgb(245, 235, 235);
    background-color: #fff !important;
    top: 0;
    bottom: 0 !important;
    width: 800px;
    height: 100px;
    margin-bottom: 0 !important;
}
.lin:hover {
    cursor: pointer;
    background-color: rgb(98, 132, 184) !important;
}
.products .col-md-6 .trans .info img {
    border: 2px solid rgb(77, 75, 75);
    width: 50px !important;
    height: 60px;
}

.info h6 {
    padding: 12px;
    border: 1px solid #ddd;
    margin-right: 90px;
}
.info {
    border: 1px solid #ddd;
}
.active {
    margin-bottom: 10px;
    margin-top: 10px;
    bottom: 0;
    top: 0;
    margin-bottom: -520px !important;
    /* margin-top: -100px; */
}
.activ {
    margin-top: -60px;
    margin-bottom: -750px !important;
    bottom: 0;
}
</style>
