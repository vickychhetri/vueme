<script setup>
import {onMounted, ref} from "vue";

let users=ref([]);

const getUsers= () =>{
axios.get('/api/users')
    .then((response)=>{
        users.value=response.data
    })
}

onMounted(()=>{
    getUsers();
})

</script>

<template>
    <div class="content-header">
        <div class="container-fluid">
            <div class="row mb-2">
                <div class="col-sm-6">
                    <h1 class="m-0">Appointments</h1>
                </div>
                <div class="col-sm-6">
                    <ol class="breadcrumb float-sm-right">
                        <li class="breadcrumb-item"><a href="#">Home</a></li>
                        <li class="breadcrumb-item active">Appointments</li>
                    </ol>
                </div>
            </div>
        </div>
    </div>

<div class="container">
    <table class="table table-striped">
        <thead>
        <tr>
            <th scope="col">#</th>
            <th scope="col">First</th>
            <th scope="col">Last</th>
            <th scope="col">Email</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="(user,index) in users" :key="user.id">
            <th scope="row">{{index+1}}</th>
            <td>{{user.name}}</td>
            <td>{{user.email}}</td>
            <td>gmsil@mdo.com</td>
        </tr>

        </tbody>
    </table>
</div>

</template>
