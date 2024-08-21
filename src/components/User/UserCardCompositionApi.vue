<script setup>
import UserAvatar from '@/components/User/UserAvatar.vue';
import {onMounted,ref}  from 'vue';

const users= ref([]);

async function fetchUser() {

    try{
            const response = await fetch('https://dummyjson.com/users?limit=10')
            const data = await response.json()
            //console.log(data)
            users= await data.users
    }catch (error){
            console.log(error)
    }
}
    

onMounted(() => {
    fetchUser()
}),
</script>

<template>
 <!--    <div v-if="users[0]" Class="user-card">
        <div>
            <img :src="users[0]?.image" alt="">
        </div>
        <h3>{{ users[0]?.firstName}} {{users[0]?.lastName }}</h3>
        <a :href="users[0]?.email">{{users[0]?.email}}</a>
    </div>
    <button @click="$event=> fetchUser()">Fetch User</button> -->

    <div v-if="users[0]" v-for="user in users" :key="user.id" class= "user-card">
        <UserAvatar :avatar= "user?.image"/>
        <h3>{{ user?.firstName+ ' '+ user?.lastName }}</h3>
        <a :href="user?.email">{{ user.email }}</a>

    </div>
</template> 

<style>
img.container{
    height: 120px;
    width: 120px;

}</style>