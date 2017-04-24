<template>
    <div id="app">
        <button @click="get()">获取用户列表</button>
        <hr>
        {{userList}}
    </div>
</template>

<script>
    import axios from 'axios'
    // var instance = axios.create({
    //     baseURL: 'http://192.168.104.243:5002/',
    //     headers: {'Content-Type': 'application/json'}
    // });
    export default {
        name: 'app',
        data () {
            return {
                userList: '',
                msg: 'Welcome to Your Vue.js App'
            }
        },
        methods: {
            get(){
//                axios.get("https://api.github.com/users/meihuixiaying").then(function (res) {
//                    console.log(res.data);
//                    this.userList = res.data;
//                }.bind(this)).catch(function (err) {
//                    console.log(err)
//                })
                axios({
                    method: 'get',
                    url: 'http://139.196.96.35:5002/v1/account/',
                    // url: "https://api.github.com/users/meihuixiaying",
                    headers: {
                        'Content-Type': 'application/json'
                        // 'Access-Control-Allow-Origin': 'http://192.168.104.35:8080'
                        // 'Access-Control-Allow-Origin': '*'
                        // 'Access-Control-Allow-Methods': 'GET, POST, PATCH, PUT, DELETE, OPTIONS',
                        // 'Access-Control-Allow-Headers': 'Origin, Content-Type, X-Auth-Token'
                    }
                }).then(function (res) {
                    console.log(res);
                    this.userList=res.data;
                }.bind(this)).catch(function (err) {
                    console.log(err);
                })
            }
        }
    }
</script>

<style lang="scss">
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
