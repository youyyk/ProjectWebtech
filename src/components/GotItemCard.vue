<template>
  <div class="card">
    <div class="card-content">
      <div class="media">
        <div class="media-content">
          <p class="title is-4">{{ itemInput.name_item }}</p>
        </div>
      </div>
      <div class="content">
        Amount: {{itemInput.amount}}
        Total: {{itemInput.price_all}}
        <div>Point Receive: {{itemInput.point_receive}}</div>
        Buy Date
        <div class="tag is-info">{{itemInput.date}}</div>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  props:{
    itemInput: Object
  },
  data() {
      return {
 
      }
  },
  methods:{
    
  }
}
</script>

<style scoped lang="scss">
.card{
  margin: 20px;
  width: 400px;
  height: 190px;
  position: relative;
  float: left;
  margin-left: 47px;
}
</style>