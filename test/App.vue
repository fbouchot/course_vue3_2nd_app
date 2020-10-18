<template>    
    <form @submit.prevent="submit" class="form">    

    {{ username }}

    <my-input 
        name="userName"
        :rules="{ required : true, min: 5}"
        :value="username.value"
        @update="update"
        type="text"
        />

    {{ password }}

    <my-input 
        name="Password"
        :rules="{ required : true, min: 10}"
         :value="password.value"
         @update="update"
         type="password"
         />

    <my-button
    color="white"
    background="darkslateblue"
    :disabled="!valid"
    ></my-button>
    </form>    
</template>
<script>
import MyButton from './myButton.vue'
import MyInput from './MyInput.vue'

export default {
    components: {
        MyButton,
        MyInput
    },
    data() {
        return {            
            username: {
                value: '',
                valid: false
            },
            password: {
                value: '',
                valid: false
            }   
        }
    },
    computed: {
        valid() {
        return this.username.valid && this.password.valid
        }
    },
    methods: {
        update(payload) {            
            this[payload.name.toLowerCase()] = {
                value: payload.value,
                valid: payload.valid
            }
        },
        submit($evt) {
            // $evt.preventDefault(); 
            console.log('Submit');
        }
    }
}
</script>
<style>
 body {
     font-family: Arial;
 }
 form {
     max-width: 400px;
     width: 50%;

 }
</style>