<script>
export default{
props:{
    avatar: String,
    imgAlt: {
          type: String,
        default: 'Test'
    }
}
}

</script>

<template>

<div class= "img-container">
<img :src="avatar ? avatar : '/avatar-placeholder.png'" :alt="imgAlt">
</div>        
    
</template>

<style scoped>
img.container{
    height: 120px;
    width: 120px;

}
</style>