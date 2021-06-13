<template>
    <div class="log-in">
        <div class="container">
            <div class="row">
                <div class="col-md-2"></div>
                <form
                    data-aos="fade-up"
                    class="col-md-8"
                    @submit.prevent="userRegistration"
                >
                    <div class="form-group row">
                        <label style="margin-right:+82px">E-Mail:</label>
                        <input
                            type="email"
                            class="form-control"
                            id="inputemail"
                            v-model="user.email"
                        />
                    </div>
                    <div class="form-group row">
                        <label>Password:</label>
                        <input
                            type="password"
                            class="form-control"
                            id="inputpassword"
                            v-model="user.password"
                        />
                    </div>
                    <div class="row but">
                        <button
                            type="submit"
                            class="btn btn-primary"
                            :disabled="!user.email || !user.password"
                        >
                            Sign Up
                        </button>
                        |
                        <button class="btn btn-primary">switch to Login</button>
                    </div>
                </form>
                <div class="col-md-2"></div>
            </div>
        </div>
    </div>
</template>
<script>
require(["aos"], function(AOS) {
    AOS.init({
        easing: "ease-in-out-sine"
    });
});
export default {
    name: "log",
    data() {
        return {
            user: {
                email: "",
                password: ""
            }
        };
    },
    methods: {
        userRegistration() {
            this.$router.push("/recipes");
        }
    }
};
</script>
<style>
.log-in .container {
    text-align: center !important;
    direction: ltr;
}
.log-in {
    background-image: url("../assets/back.jpg");
    box-sizing: border-box;
    width: 700px;
    height: 320px;
    text-align: center;
    margin: 180px;
    margin-left: 180px !important;
    border: 1px solid #ddd;
    padding: 10px 15px;
}
@media (max-width: 578px) {
    .log-in {
        margin-left: -190px !important;
        width: 400px !important;
        height: 280px !important;
        margin-right: 160px !important;
        text-align: center !important;
    }
}
@media (max-width: 1335px) {
    .log-in {
        margin-left: 1px !important;
        width: 600px !important;
        height: 320px;
        text-align: center !important;
    }
}
@media (min-width: 1023px) {
    .log-in {
        margin-left: 100px !important;
        width: 600px !important;
        height: 320px;
        text-align: center !important;
    }
}
.log-in .form-group {
    margin-top: 20px;
    text-align: center !important;
}
.log-in label {
    font-weight: bold;
    font-size: 25px;
    margin-right: 40px;
}
.log-in input {
    width: 400px;
    height: 40px;
    border: 1px solid rgb(236, 185, 185);
}
.log-in .row button {
    color: honeydew;
    font-weight: bold;
    height: 40px;
    width: 160px;
    margin: 5px;
    background-color: rgb(80, 148, 204);
    border-radius: 5px;
    font-size: 18px;
}
.but button:disabled {
    opacity: 0.4 !important;
    cursor: no-drop !important;
}
</style>
