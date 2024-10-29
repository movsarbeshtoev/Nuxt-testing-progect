<script >
    export default {
        props:{
            post:Object
        }
    }  
    
</script>

<template>
    <div>
         <div class="postContainer">
            <h1>{{post.title}}</h1>
            <p>{{post.body}}</p>
        </div>
        <div class="postDetails">
            <postReaction :likes="post.likes" :dislikes="post.dislikes"/>
            <NuxtLink class="link" :to="`/comments/${post.id}`">Open сomments</NuxtLink>
            <span>Today</span>
            <div>
                <span>tag</span>
                <span>tag</span>
                <span>tag</span>
            </div>
        </div>
    </div>

</template>

<style scoped>
    .postContainer{
        display: flex;
        flex-direction: column;
        align-items: flex-start;
    }

    .postDetails{
        display: flex;
        align-items: center;
        gap: 8px;
    }
    
    .link{
        color:rgb(255, 107, 0);;
        position: relative;
        text-decoration: none;
        border-bottom: 1px ;
    }

/* .link::after {
  content: "";
  position: absolute;
  bottom: -4px; 
  left: 0;
  width: 100%;
  height: 1px;
  background-color: rgba(255, 107, 0, 0.3);
} */
</style>