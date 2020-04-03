<template>
    <div class="row">
        <div class="col-md-6 offset-md-3">
            <div class="card my-2">
                <div class="card-body">
                    <h3 class="text-center my-3">User Credentials</h3>
                    <div class="form-group">
                    <input v-model="name" type="test" placeholder="Name" class="form-control">
                    </div>
                    <div class="form-group">
                    <input v-model="pnumber" type="number" placeholder="Phone Number" class="form-control">
                    </div>
                    <div class="form-group">
                    <input v-model="username" type="text" placeholder="Username" class="form-control">
                    </div>
                    <div class="form-group">
                    <input v-model="email" type="mail" placeholder="Email" class="form-control">
                    </div>
                    <div class="form-group">
                    <input v-model="password" type="password" placeholder="Password" class="form-control">
                    </div>
                    <div class="form-group text-center">
                    <button @click="registerUser()" class="btn btn-success">Signup</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Axios from 'axios';
export default {
    data(){
        return{
            name: '',
            pnumber: '',
            username: '', 
            email: '',
            password: ''
        }
    },
    methods:{
        registerUser(){
            Axios.post('https://react-blog-api.bahdcasts.com/api/auth/register',{
                name: this.name,
                pnumber: this.pnumber,
                username: this.username,
                email: this.email,
                password: this.password
            }).then((response) => {
                const { data } = response.data;
                localStorage.setItem('auth', JSON.stringify(data))
                this.$root.auth = data;

                this.$router.push('home');
            })
        }
    }
};
</script>
