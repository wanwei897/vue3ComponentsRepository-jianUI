<template>
  <div class="appWrap">
    <span class="showName" v-for="item in 50" :key="item">
      {{jianUI.faker.getName()}} 
      {{jianUI.faker.getAge()}} 
      {{jianUI.faker.getAddress()}} 
      {{jianUI.faker.getDate()}} 
      {{jianUI.faker.getEmail()}} 
      {{jianUI.faker.getTelephone()}} 
    </span>
  </div>
</template>

<script>
// import loading from '@/components/loading/loading'
// import $ from 'jquery'
// import _ from 'lodash'
export default {
  name: 'App',
  components: {
  },
  props:{
  },

  data() {
    return {
    }
  },
  methods: {
  },
  created() {
  },
  mounted() {
    var myWorker = this.jianUI.worker.createWorker(() => {
      self.onmessage = (e) => {
        console.log(e.data)
        if(e.data === 'Are you ready?') {
          console.log('Im ready.');
          self.close();
        }
      }
    })
    myWorker.postMessage('Are you ready?')
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
*{
  margin: 0;
  padding: 0;
}
li{
  list-style: none;
}

.appWrap{
  position: relative;
  border: 1px solid #ac7d11;
  white-space: normal;
  margin: 40px 40px;
}
.showName{
  display: inline-block;
  background: rgb(223, 177, 177);
  margin-left: 10px;
}
</style>
