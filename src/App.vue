<template>
  <div id="app">
    <h1>Job Board </h1>
    
  </div>
</template>

<script>


export default {
  name: "app",
  data() {
    return {
      jobs: [],
    };
  },
  methods: {
    getJobs: function() {
      fetch("https://jobs.github.com/positions.json?description=python&location=new+york")
      .then(res => res.json())
      .then(jobData => {
        jobData.forEach(job => (job.isStarred = false));
        this.jobs = jobData;
      })
    }
  },
  mounted() {
    this.getJobs();
  }

}
</script>

<style>

</style>