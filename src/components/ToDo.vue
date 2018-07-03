<template>
  <div id="app">
      <h2>To Do List</h2>
      
      <input type="text" 
        v-model.trim="text" 
        @keyup.enter="submit(text)" 
        placeholder="Add A Target On The List"/>

      <ul>
          <div v-if="list.length === 0" class="empty">
              No target on this list.
          </div>
          <li v-for="(item, index) in list" :key="index">{{ item }} 
              <span @click="remove(index)">–</span>
          </li>
      </ul>
  </div>
</template>

<script>
export default {
  name: 'ToDoList',
  data () {
    return {
      text: '',
      list: []
    }
  },
  methods: {
    submit(todo){
        todo && 
            this.list.push(todo) 
            this.text = ''

    },
    remove(index){
        this.list.splice(index, 1)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
    font-weight: normal;
}
ul {
    list-style-type: none;
    width: 40%;
    border: 2px solid rgb(205, 238, 208);
    margin: 20px auto;
    border-radius: 8px;
    padding: 0 8px;
}
li {
    display: block;
    padding: 10px 8px;
    background-image: linear-gradient(
        to right,
        rgb(190, 211, 190) 35%,
        rgba(255, 255, 255, 0) 0%
    );
    background-position: bottom;
    background-size: 12px 1px;
    background-repeat: repeat-x;
}
li span {
    font-weight: bolder;
    color: #fff;
    background: #dc1e1e;
    width: 20px;
    display: block;
    height: 20px;
    border-radius: 50%;
    float: right;
    cursor: pointer;
    font-size: small;
    border: 1px solid #333;
}
li:last-child {
    background: none;
}
a {
    color: #42b983;
}
input {
    padding: 8px;
    color: #333;
    width: 40%;
    line-height: 30px;
    font-size: 20px;
    text-align: center;
    letter-spacing: 1px;
    border-radius: 3px;
    border: 1px solid transparent;
    border-top: none;
    border-bottom: 1px solid #DDD;
    box-shadow: inset 0 1px 5px rgba(0,0,0,.2), 0 -1px 1px #FFF, 0 1px 0 #FFF;
}
.empty {
    padding: 30px 0;
}
</style>
