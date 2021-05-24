<template>
  <div class="part">
    <h1><fa class="icon" icon="code" />Projets</h1>
    <div class="list">
      
    </div>
  </div>
</template>

<script>
export default {
  name: "Projects",
  data() {
    return {
      data:[
        
      ]
    }
  }
};
</script>

<style scoped>
.part {
  background: #fdfffc;
}

.list {
  margin-top: 25px;
  width: 100%;

  display: flex;
  flex-direction: row;
  justify-content: space-between;
  flex-wrap: wrap;
  align-items: flex-start;
  align-content: center;
}
</style>