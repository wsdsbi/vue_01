<template>
    <div>
        {{ message }}
        <button @click="notice">gegyab</button>
    </div>    
</template>
<script>
export default {
    props:['msg'],
    data(){
        return{
            message:this.msg
        }
    },
    methods:{
        notice(){
        this.message= this.message.slice(0,this.message.length-1)
        }
    }
}
</script>

<style>

</style>