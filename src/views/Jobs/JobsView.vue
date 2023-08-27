<template>
  <div v-if="jobs.length">
    <h1>Jobs</h1>
    <div v-for="job in jobs" :key="job.id" class="job">
        <router-link :to="{name:'jobsDetails', params: { id: job.id }}">
            <h2>{{ job.title }}</h2>
        </router-link>
    </div>
  </div>
  <div v-else>
    <p>Lodaing Jobs...</p>
  </div>
</template>

<script >
export default {
    data(){
        return{
            jobs:[
                // {title: 'Web Developer', id: 1, ditails: 'lorem'},
                // {title: 'App Developer', id: 2, ditails: 'lorem'},
                // {title: 'UX Developer', id: 3, ditails: 'lorem'},
            ]
        }
    },
    mounted(){
        fetch('http://localhost:3000/jobs')
            .then((res) => res.json())
            .then(data => this.jobs = data)
            .catch(err => console.log(err.message))
    }

}
</script>

<style>
.job h2{
    background: #f4f4f4;
    padding: 20px;
    border-radius: 10px;
    margin: 10px auto;
    max-width: 600px;
    cursor: pointer;
    color: #444;
}
.job h2:hover{
    background: #ddd;
}
.job a{
    text-decoration: none;
}
</style>