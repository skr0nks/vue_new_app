<template>
    <div class="app">
        <form @submit.prevent>
            <h4>Создание поста</h4>
            <input v-bind:value="title" @input="title = $event.target.value" class="input" type="text" placeholder="Название">
            <input v-bind:value="body" @input = "body = $event.target.value" class="input" type="text" placeholder="Описание">
            <button class="btn" @click="createPost">Создать</button>
        </form>
<div class="post" v-for="post in posts">
    <div><strong>Название:</strong>{{post.title}}</div> 
    <div><strong>Описание:</strong>{{post.body}}</div> 

</div>
    </div>
</template>

<script>
export default{
    data(){
        return{
            posts:[
                {id:1,title:'Javascript',body:"Описание поста 1"},
                {id:2,title:'Javascript',body:'Описание поста 2'},
                {id:3,title:'Javascript',body:'Описание поста 3'},
            ],
            title:'',
            body:'',
        }
    },
    methods:{
        createPost(){
            const newPost = {
                id: Date.now(),
                title:this.title,
                body:this.body,
            }
            this.posts.push(newPost);
            this.title = '',
            this.body = '';
        },
    }
}
</script>

<style>
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
.app{
    padding: 20px;
}
.post{
    padding: 15px;
    border: 3px solid rgb(158, 166, 224);
    margin: 15px 1px;
}
form{
    display: flex;
    flex-direction: column;
}
.input{
    width: 100%;
    border: 3px solid rgb(158, 166, 224);
    padding: 10px 15px;
    margin-top: 15px;
}
.btn{
    margin-top: 15px;
    align-self: flex-end;
    padding: 10px 15px;
    background: none;
    border: 3px solid rgb(158, 166, 224);
    color: rgb(158, 166, 224);
}

</style>