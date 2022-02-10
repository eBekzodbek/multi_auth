<template>
    <div class="container">
        <div class="row align-items-center height-100vh">
            <div class="col-4 mx-auto max-width-none">
                <div class="card w-400 border-0 login-width">
                    <div class="card-body">
                        <div class="form-group col-12">
                            <h5>Create an account</h5>
                        </div>
                    </div>
                    <ValidationObserver v-slot="{ handleSubmit }">
                        <form @submit.prevent="handleSubmit(submitRegister)">
                            <div class="mb-3 p-2">
                                <label for="name">Name</label>
                                <ValidationProvider name="name" rules="required" v-slot="{errors}">
                                    <input type="text" id="name"
                                           v-model="name" class="form-control"
                                           placeholder="Enter your name"
                                    />
                                    <span class="invalid-feedback d-block">
                                        {{errors[0]}}
                                    </span>
                                </ValidationProvider>
                            </div>
                            <div class="mb-3 p-2">
                                <label for="email">Email</label>
                                <validation-provider name="Email" rules="required|email" v-slot="{errors}">
                                    <input
                                        type="email" id="email"
                                        v-model="email" class="form-control"
                                        placeholder="Enter your email"
                                    />
                                    <span class="invalid-feedback d-block">
                                        {{errors[0]}}
                                    </span>
                                </validation-provider>
                            </div>
                            <div class="mb-3 p-2">
                                <label for="password">Password</label>
                                <validation-provider name="password" rules="required|min:8" vid="confirmation" v-slot="{errors}">
                                    <input type="password" id="password"
                                           v-model="password" class="form-control"
                                           placeholder="Enter your password"
                                    />
                                    <span class="invalid-feedback d-block">{{errors[0]}}</span>
                                </validation-provider>
                            </div>
                            <div class="mb-3 p-2">
                                <label for="password-confirmation">Confirm Password</label>
                                <validation-provider name="password" rules="required|min:8|confirmed:confirmation" v-slot="{errors}">
                                    <input type="password" id="password-confirmation"
                                           v-model="password_confirmation" class="form-control"
                                           placeholder="Enter your password confirmation"
                                    />
                                    <span class="invalid-feedback d-block">{{errors[0]}}</span>
                                </validation-provider>
                            </div>

                            <div class="d-grid gap-2">
                                <button class="btn btn-primary btn-block" type="submit">Sign up</button>
                            </div>
                            <div class="mb-3 p-2">
                                <div class="mb-3">
                                    Already have an account?
                                    <a href="/login">login</a>
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
    name: "RegisterComponent",
    data () {
        return {
            name: '',
            email: '',
            password: '',
            password_confirmation: '',
        }
    },
    mounted() {
        console.log('register component')
    },

    methods: {
        submitRegister(){
            axios.post('/register', {
                name: this.name,
                email: this.email,
                password: this.password,
                password_confirmation: this.password_confirmation,
            }).then((res) => {
                location.href = '/home'
            }).catch((error) => {
                console.log('error')
            })
        }
    }

}
</script>

<style scoped>

</style>
