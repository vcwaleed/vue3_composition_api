<template>
    <div>
        <h1>Home Page</h1>
        <p>Welcome to the Home Page</p>
        <p>Count: {{count}}</p>
        {{ arrayOfEmojis }}

    </div>
    <div>
        <button v-on:click="increment">Counter</button>
    </div>
</template>
<script>
import {onMounted ,ref,watch,computed} from 'vue'
export default {
    name: 'HomePage',
    props:{
        emoji:{
            type: String,
            default: '🚀'
        }
    },
    setup(props) {
        console.log(props.emoji)
        onMounted(() => {
            console.log('Component is mounted')
        })
        const count = ref(4)
        const increment =()=>{
            count.value++
        }
        watch(count,(current,previous)=>{
            console.log(`Count changed from ${previous} to ${current}`)
           
        })

        const arrayOfEmojis =computed (()=>
    Array.from(new Array(count.value),()=>props.emoji).join(''))

        return {
            count,
            increment,
            arrayOfEmojis
        }
    }

}
</script>