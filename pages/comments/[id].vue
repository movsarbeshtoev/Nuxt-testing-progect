<script setup>
    const comments = reactive([])
    const post = ref({})
    
    
    const id_post = useRoute().params.id
        onMounted(async()=>{

            try {
                const postRes = await fetch(`https://dummyjson.com/posts/${id_post}`)
                const postData = await postRes.json()
                post.value = postData;
                console.log(post.value,"post");
            } catch (error) {
                console.log(error);
            }
            try {
                const response = await fetch(`https://dummyjson.com/posts/${id_post}/comments`,{method:"GET"})
                const data = await response.json()
                comments.push(...data.comments)
                console.log(comments,"comments");
            } catch (error) {
                console.log(error);
            }
            }
        ) 

        
            const handleDeleteClick = (id) => {
                const index = comments.findIndex(comment => comment.id === id);
                
                if (index !== -1) {
                comments.splice(index, 1);
                }

                console.log(comments);
            
        }

        
        
    
</script>

<template>

    <div>
        <PostItem :post="post"/>
        <h1>Comments</h1>
        <div class="commentsContainer">
            <ul v-for="comment in comments " :key="comment.id">
                <li>
                    <div class="commentItem">
                        <svg width="46" height="46" viewBox="0 0 46 46" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <circle cx="23" cy="23" r="20.5" stroke="#05090E" stroke-width="5" stroke-dasharray="20 5"/>
                        </svg>
                        <div class="commentDetails">
                            <span>{{comment.name || "Anonymous"}}</span>
                            <span>{{comment.body}}</span>
                            <div class="commentFooter">
                                <span>Today</span>
                                <span @click="handleDeleteClick(comment.id)" >Delete</span>
                            </div>
                        </div>
                    </div>
                </li>
            </ul>
        </div>
    </div>
</template>

<style scoped>
    .commentsContainer{
        display: flex;
        flex-direction: column;
        gap:24px;
    }

    .commentItem{
        display: flex;
        gap:12px;
        align-items: flex-start;
    }

    .commentDetails{
        display: flex;
       flex-direction: column;
       gap:10px;
       align-items: flex-start;
    }

    .commentFooter{
        display: flex;
        align-items: center;
        gap:20px;
    }

    li{
       list-style: none; 

    }
</style>