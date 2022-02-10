<template>
    <div class="container">
        <div class="row align-items-center height-100vh">
            <div class="col-4 mx-auto max-width-none">
                <div class="card w-400 border-0 login-width">
                    <div class="card-body">
                        <div class="form-group col-12">
                            <h5>Sign into your account</h5>
                        </div>
                    </div>
                    <ValidationObserver v-slot="{ handleSubmit }">
                        <form @submit.prevent="handleSubmit(userLogin)">
                            <div class="mb-3 p-2">
                                <label for="email">Email</label>
                                <ValidationProvider name="Email" rules="required|email" v-slot="{errors}">
                                    <input type="email" id="email"
                                           v-model="email" class="form-control"
                                           placeholder="Enter your email"
                                    />
                                    <span class="invalid-feedback d-block" >{{errors[0]}}</span>
                                </ValidationProvider>
                            </div>
                            <div class="mb-3 p-2">
                                <label for="password">Password</label>
                                <validation-provider name="password" rules="required|min:8" v-slot="{errors}">
                                    <input type="password" id="password"
                                           v-model="password" class="form-control"
                                           placeholder="Enter your password"
                                    />
                                    <span class="invalid-feedback d-block">{{errors[0]}}</span>
                                </validation-provider>
                            </div>
                            <div class="mb-3 flexbox py-3 form-style p-2">
                                <div class="custom-control custom-checkbox pl-0">
                                    <input type="checkbox" name="remember" /> Remember Me
                                </div>
                            </div>
                            <div class="d-grid gap-2">
                                <button class="btn btn-primary btn-block" type="submit">Login</button>
                            </div>
                            <div class="mb-3 p-2">
                                <div class="mb-3">
                                    Don't have an account?
                                    <a href="/register">Create Account</a>
                                </div>
                            </div>
                        </form>
                    </ValidationObserver>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "LoginComponent",
    data () {
        return {
            email: '',
            password: '',
        }
    },

    methods: {
        userLogin(){
            axios.post('/login', {
                email: this.email,
                password: this.password
            }).then((res) => {
               location.href = '/home'
            }).catch((e) => {

            })
        }
    }
}
</script>

<style scoped>

</style>
