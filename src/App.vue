<template>
  <div id="app">
    <NavBar class="navbar" title="毒鸡汤">  </NavBar>
    <van-swipe class="my-swipe" indicator-color="white">
       <van-swipe-item   v-bind:key="item" v-for="(item) in this.infos">
       
          <div class="swipe-item">
            {{item}}
            </div>  
       </van-swipe-item>
 
     </van-swipe>

    <van-tabbar v-model="active" class="tabbar">
  <van-button type="primary" class="btnChange" @click="changeInfos()">换几碗试试</van-button>
 
</van-tabbar>
  

  </div>
</template>

<script>
import 'vant/lib/index.css';
import 'vant/lib/nav-bar/style';
import './data.js'
import saveDatas from './data.js'
import { NavBar} from "vant";



export default {
  name: 'App',
  components: {
    NavBar,
    
  },
  mounted() {

  this.changeInfos();

  
  

  
},
methods:{
  changeInfos(){
    this.infos=[];
    let n=saveDatas.length;
  for(let i=0;i<10;i++){
    let m=Math.floor(Math.random()*n);
      this.infos.push(saveDatas[m].data);
  }
  console.log(this.infos);
  },
},
data() {
    return {
      allDatas:saveDatas,
      infos:[],
    }
  },

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}
.van-nav-bar__title
{
  font-weight: 600;
}
.my-swipe
{
  position: absolute;
  top:46px;
  bottom: 46px;
  background-color: #f5f5f5;
  width: 100%;
}
 

  .swipe-item
  {
    font-size: 24px;
    line-height: 48px;
    text-align: center;
    background-color: rgb(240, 240, 240);
    height: 100%;
    word-wrap: break-word;
    padding: 24px;
    text-indent: 2em;
    display: flex;
    justify-content: center;
    align-items: center;
    
  }
  .tabbar
  {
    position: absolute;
    height: 46px;
    bottom: 0px;
    width: 100%;

  }
  .btnChange
  {
     position: absolute;
     left: calc(50% - 60px);
     width: 120px;
     height: 40px;
     top: 3px;
    
  }
  

</style>
