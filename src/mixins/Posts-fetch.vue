<script>
import axios from 'axios'

export default {
    methods: {
        getPosts(){
            return new Promise((resolve, reject) =>{
                axios('https://jsonplaceholder.typicode.com/posts', {
                    method: 'GET'
                })
                .then((res) => {
                    resolve(res.data)
                })
                .then((err) => {
                    reject(err)
                })
            })
        },

        sendPost(title, content){
            return new Promise((resolve, reject) =>{
                axios.post('https://jsonplaceholder.typicode.com/posts', {
                    headers: {
                     'content-type': 'application/json'
                    },
                    title: title,
                    body: content,
                    userId: 11
                })
                .then((res) => {
                    resolve(res.data)
                })
                .then((err) => {
                    reject(err)
                })
            })
        }

    }
}
</script>