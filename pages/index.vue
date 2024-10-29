<script setup lang="ts">
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


    
        const posts= reactive<Post[]>([])
        
        onMounted(async ()=>{
            
          const response = await fetch("https://dummyjson.com/posts?limit=5")
          const data =await response.json()
          posts.push(...data.posts)
          console.log(posts[0]);
          
        })
    


</script>

<template>
    <div>
        <div v-for="post in posts" :key="post.id">
        <PostItem :post="post"/>
        </div>
    </div>
</template>