<template>
    <div>
        <v-row class="justify-center">
            <v-col md="8">
                <v-form ref="form" v-model="valid">
                    <v-row class="py-4">
                        <v-col class="justify-center">
                            <h2 class="text-h3 font-weight-medium ">Your review</h2>
                        </v-col>
                    </v-row>

                    <v-row>
                        <v-col md="6">
                            <v-text-field 
                                v-model="name"
                                :counter="12"
                                :rules="nameRules"
                                label="Full name"
                                required
                            >
                            </v-text-field>
                        </v-col>

                        <v-col md="6">
                            <v-text-field
                                v-model="email"
                                :counter="25"
                                :rules="emailRules"
                                label="E-mail"
                                required
                            >

                            </v-text-field>
                        </v-col>

                        <v-col md="12">
                            <v-textarea
                                v-model="message"
                                :counter="500"
                                label="Your message to us"
                                required
                            ></v-textarea>
                        </v-col>

                        <v-col md="6">
                            <v-btn
                                :disabled = "!valid"
                                color="warning"
                                @click="sendForm"
                            >
                                Send Comment
                            </v-btn>
                        </v-col>
                    </v-row>
                </v-form>
            </v-col>
        </v-row>
    </div>
</template>
<script>
export default {
    methods:{
        sendForm(){
            this.$refs.form.validate();
            alert('From is sended')
        }
    },
    data(){
        return{
            valid: false,
            name: '',
            nameRules:[
                v => !!v || 'Name is required',
                v => v.length <= 12 || 'Name must be less than 12 characters',
            ],
            email: '',
            emailRules:[
                v => !!v || 'Email is required',
                v => /.+@.+/.test(v) || 'Email must be valid'
            ],
            message:''
        }
    }
}
</script>