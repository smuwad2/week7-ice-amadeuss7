<script>
    import axios from 'axios';
    
export default {
// add code here
    data() {
           return {
               subject: '',
               entry: '',
               mood: 'Happy',
               moods: ['Happy', 'Sad', 'Angry', 'Excited', 'Calm']
           }
       },
       methods: {
           async submitPost() {
               if (!this.subject || !this.entry || !this.mood) return;
               await axios.post('http://localhost:3000/addPost', {
                   subject: this.subject,
                   entry: this.entry,
                   mood: this.mood
               });
               this.subject = '';
               this.entry = '';
               this.mood = 'Happy';
           }
       }
    }
</script>

<template>
    <div class="table m-2">
        <h3>Add a New Blog Post</h3>

        Subject: <input type='text' size='30' v-model='subject' required>
        <br>

        Entry: <br>
        <textarea name='entry' cols='80' rows='5' v-model='entry' required></textarea>
        <br>


        Mood:
        <select v-model="mood">
            <option v-for="m in moods" :key="m">{{ m }}</option>
        </select>

        <br>

        <br>
        <button @click="submitPost">Submit New Post</button>

        <hr> Click  <a><router-link to="/ViewPosts/">here</router-link></a>  to return to Main Page
       
    </div>
</template>

