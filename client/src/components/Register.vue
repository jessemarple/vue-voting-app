<template>
    <div>
        <v-layout row>
            <v-flex xs6 offset-xs3>
                <v-card>
                    <v-card-title>
                        <v-container>
                            <h4>Register</h4>
                        </v-container>
                        <v-container v-if='loginError'>
                            <h5>Something went wrong. Please try again.</h5>
                        </v-container>
                    </v-card-title>
                    <v-card-text>
                        <v-container>
                            <v-form>
                                <v-layout row>
                                    <v-flex xs12>
                                        <v-text-field
                                        v-model='username'
                                        name='username'
                                        label='Username'
                                        type='text'
                                        required
                                        ></v-text-field>
                                    </v-flex>
                                </v-layout>
                                <v-layout row>
                                    <v-flex>
                                        <v-text-field
                                        v-model='password'
                                        name='password'
                                        type='password'
                                        label='Password'
                                        required
                                        ></v-text-field>
                                    </v-flex>
                                </v-layout>
                                <v-layout row>
                                    <v-flex xs4 offset-xs4>
                                        <v-btn
                                        @click='register'
                                        block
                                        large
                                        class='mt-4 orange darken-4 white--text'
                                        type='submit'
                                        >
                                        Register
                                        </v-btn>
                                    </v-flex>
                                </v-layout>
                            </v-form>
                        </v-container>
                    </v-card-text>
                </v-card>
            </v-flex>
        </v-layout>
    </div>
</template>

<script>
export default {
    data() {
        return {
            username: '',
            password: '',
            loginError: ''
        }
    },
    methods: {
        async register() {
            try {
                await this.$store.dispatch('register', {
                username: this.username,
                password: this.password
            });
            
            this.$router.push('/');
            } catch(err) {
                this.loginError = true;
                return err;
            }
            
        }
    }
}
</script>

