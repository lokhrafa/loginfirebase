<template>
 <v-container>
     
    <v-layout row>
        <v-flex xs12 sm6 offset-sm3>
        <v-card>
            <v-card-text>
                <v-container>
                    <form @submit.prevent="onSignup">
                    <v-layout row>
                        <v-flex xs12>
                            <v-text-field
                            name="email"
                            label="Mail"
                            id="email"
                            v-model="email"
                            type="email"
                            required></v-text-field>
                        </v-flex>
                    </v-layout>
                    <v-layout row>
                        <v-flex xs12>
                            <v-text-field
                            name="password"
                            label="Password"
                            id="password"
                            v-model="password"
                            type="password"
                            required> </v-text-field>
                        </v-flex>
                    </v-layout>
                    <v-layout row>
                        <v-flex xs12>
                            <v-text-field
                            name="confirmPassword"
                            label="Confirm Password"
                            id="confirmPassword"
                            v-model="confirmPassword"
                            type="password"
                            :rules="[comparePasswords]"></v-text-field>
                        </v-flex>
                    </v-layout>
                    <v-layout row>
                        <v-flex xs12>
                            <v-btn type="submit">Sign up </v-btn>
                        </v-flex>
                    </v-layout>
                    </form>
                </v-container>
            </v-card-text>
        </v-card>
        </v-flex>
     </v-layout>
 </v-container>
</template>

<script>
export default {
     /* eslint-disable */
    data(){
         /* eslint-disable */
        return {
        email:'',
        password: '',
        confirmPassword:''
 /* eslint-disable */
        }
        
    },
    computed: {
         /* eslint-disable */
        comparePasswords(){
            return this.password !== this.confirmPassword ? 'Passwords dot not match' : ''
             /* eslint-disable */
        },
         /* eslint-disable */
        user(){
             /* eslint-disable */
            return this.$store.getters.user
        }
    },
     /* eslint-disable */
    watch: {
         /* eslint-disable */
        user(value){
             /* eslint-disable */
            if (value !== null && value !== undefined){
                this.$router.push('/')
            }
        }
    },
    methods: {
         /* eslint-disable */
        onSignup(){
            this.$store.dispatch('signUserUp', {email: this.email, password: this.password})
        }
    }
}
</script>

