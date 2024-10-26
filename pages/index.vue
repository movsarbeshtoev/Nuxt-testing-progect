<script lang="ts">
interface Post {
  id: number
  title: string
  body: string
  tags: string[]
  reactions: {
    likes: number
    dislikes: number
  }
  views: number
  userId: number
}

export default {
    setup(){
        const posts= reactive<Post[]>([])
        
        onMounted(async ()=>{
            
          const response = await fetch("https://dummyjson.com/posts")
          const data =await response.json()
          posts.push(...data.posts)
          console.log(posts);
          
        })
    }
}
head:{
    title: 'Posts'}
</script>

<template>
    <div>
        <h1>Posts</h1>
        <PostItem />
    </div>
</template>