<script setup>
import axios from 'axios'
import { reactive } from 'vue'
let obj = reactive({
    title: "",
    text: "",
    subcategory: 1,
    description: "",
    postImg: null,
    phone: 1,
    dateH: "",
    dateY: "",
    fullname: "",
    type: "",
    job: "",
})
let ok = {
    title: "string",
    text: "stringstringstringstringstringstringstringstringstringstringstringstringstringstringstringstringstringstringstringstring",
    subcategory: 1,
    description: "string",
    postImg: obj.postImg,
    phone: 998900093787,
    dateH: "string",
    dateY: "string",
    fullname: "string",
    type: "string",
    job: "string",
}
let POST = () => {
    console.log(obj);
    axios.post('https://imthon.onrender.com/posts' , obj,{
        headers: {
            'Content-Type' : 'multipart/form-data'
        }
    }).then(res => console.log(res))
    .catch((error) => console.log(error))
}



function postImg(e){
    let [file] = e.target.files
    obj.postImg = file
}
</script>
<template>
    <section class="hero">
        <div class="container">
            <div class="hero__wrapper">
                <input type="text" v-model="obj.title" placeholder="title">
                <input type="text" v-model="obj.text" placeholder="text">
                <input type="number" v-model="obj.subcategory" placeholder="subcategory">
                <input type="text" v-model="obj.description" placeholder="description">
                <input type="file" @change="postImg">
                <input type="number" v-model="obj.phone" placeholder="phone">
                <input type="text" v-model="obj.dateH" placeholder="dateH">
                <input type="text" v-model="obj.dateY" placeholder="dateY">
                <input type="text" v-model="obj.fullname" placeholder="fullname">
                <input type="text" v-model="obj.type" placeholder="type">
                <input type="text" v-model="obj.job" placeholder="job">
                <button class="hero__btn" @click="POST">POST</button>
            </div>
        </div>
    </section>
</template>