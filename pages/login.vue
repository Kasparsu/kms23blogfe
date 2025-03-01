<script setup>
    import axios from 'axios';
    let router = useRouter();
    let form = ref({
        email: '',
        password: '',
    });
    
    function login(){
        axios.defaults.withCredentials = true;
        axios.defaults.withXSRFToken = true;
        axios.get('http://localhost:8000/sanctum/csrf-cookie').then(response => {
            console.log(response);
            axios.post('http://localhost:8000/api/login', form.value).then(res => {
                console.log(res.data);
                axios.get('http://localhost:8000/api/user', form.value).then(res => {
                    console.log(res.data);
                    router.push('/');
                });
            //router.go('/');
            });
        });
        
    }
</script>

<template>
    <div class="container">
        <section>
            <div class="card">
                <div class="card-content content">
                    <h1>Login</h1>
                    
                    <b-field label="Email">
                        <b-input v-model="form.email" type="email" maxlength="255"></b-input>
                    </b-field>

                    <b-field label="Password">
                        <b-input v-model="form.password" type="password" maxlength="255"></b-input>
                    </b-field>

                    <b-button type="is-primary" @click="login">Login</b-button>
                </div>
            </div>
        </section>
    </div>
</template>