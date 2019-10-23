<template>
    <div id="fetchData" class="container">
        <p>this is where I'll fetch data</p>
        <br />
        <div v-for="user in users" v-bind:key="user.id" class="item">
            <h2>{{ user.name }}</h2>
            <p>Email: {{user.email}}</p>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'FetchData',
    data() {
        return {
            users: null
        }
    },
    mounted () {
        axios.get('https://iadtprofessionalpractice.herokuapp.com/api/users')
        .then(response => (this.users = response.data))

    }
}

</script>

<style>
    .container {
       width: 100%;
       display: flex;
       flex-wrap: wrap;
       justify-content: center
    }
    .item {
        width: 80%;
    }
    .item:nth-child(odd) {
        background-color: #e6e6e67d;
    }
</style>


