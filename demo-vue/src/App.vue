
<template>
  <div>
    <button @click="showPopup = true">Show Popup</button>
    <Popup v-show="showPopup" @closePopup="closePop"/>
    <h3>App component username - {{name}}</h3>
    <ComponentC/>
    <WatchersDemo></WatchersDemo>
    <ComputedPropDemo></ComputedPropDemo>
    <ComponentPropsDemo name="Benjamin"/>
    <ComponentPropsDemo name="Jhonson"/>
    <ComponentPropsDemo name="Robert"/>
     <ComponentPropsDemo :name="info.name"/>
     <PropTypesDemo id="my-article" :likes="50" :is-published="true"/>
  <componentA></componentA>
  <form1></form1>
  
  <div>{{ greet }} {{ name }}</div>
  <div v-html="job"></div>
  <h2 v-bind:id="headingId">Heading</h2>
  <button v-bind:disabled="isDisabled">Bind</button>
  <h3 class="underline">Underlined Text</h3>
  <h2 v-bind:class="status">Status</h2>
  <h2 v-bind:class="isPromoted && 'promoted'">Promoted Movie</h2>
  <h2 v-bind:class="isSoldout ? 'sold-out' : 'new'">Soldout? movie</h2>
  <h2 v-bind:class="['new','promoted']">Newly promoted movie</h2>
  <h2 v-bind:class="[isPromoted && 'promoted',isSoldout ? 'sold-out' : 'new']">Array conditional movie</h2>
  <h2 v-bind:class="{
    promoted:isPromoted,
    new: !isSoldout,
    'sold-out': isSoldout

  }">Object conditional movie</h2>
  <h2 v-bind:style="{
    color:highlightColor,
    'font-size':`${headerSize}px`,
    padding:'20px'
  }">Inline styles</h2>
  <h2 v-bind:style="headerStyleObject">Style Object</h2>
  <h2 :style="[shortHandStyleObject]">Shorthand V bind</h2>
  <p v-if="num === 0">Number {{num}}</p>
  <p v-else>Number is {{num}}</p>

  <template v-if="display">
    <h2>Checking conditional rendering</h2>
  </template>
  <h2 v-show="showElement">Using v-show</h2>
  <ul v-for="(name,index) in tech" :key="name" :style="{listStyleType:'none'}">
    <li>{{index +1}} - {{name}}</li>
  </ul>
  <h2 v-for="(h,index) in hero" :key="h.tile">{{index}} . {{h.tile}} ---> {{h.name}}</h2>
  <div v-for="actor in actors" :key="actor.name">
    <h2>{{actor.name}}</h2>
    <h3 v-for="(movie,index) in actor.movies" :key="index">{{movie}}</h3>
  </div>
  <h2 v-for="(value,key,index) in info" :key="value">{{index}} .. {{key}}  .. {{value}}</h2>
  <template v-for="name in conditionalNames" :key="name" >
    <h2 v-if="name === 'Ram'">{{name}}</h2>
    
  </template>
  <h2>Add currying method - {{add(2)(4)}}</h2>
  <h2>Multiply by five - {{ mulByFive(2)}}</h2>
  </div>
  
</template>

<script>
import componentA from './components/ComponentA.vue';
import form1 from './components/Form1';
import ComputedPropDemo from './components/ComputedPropDemo';
import WatchersDemo from './components/WatchersDemo';
import ComponentPropsDemo from './components/ComponentPropsDemo';
import PropTypesDemo from './components/PropTypesDemo';
import ComponentC from './components/ProvideandInjectDemo/ComponentC';
import Popup from './components/ComponentsEventsDemo/Popup'
export default { 
  name: 'App',
  components:{componentA,form1,ComputedPropDemo,WatchersDemo,ComponentPropsDemo,PropTypesDemo,ComponentC,Popup},
  data(){
    return {
      greet:'Hello',
      name:"Abhishek",
      job:'<b>Developer</b>',
      headingId:'heading',
      isDisabled:false,
      status:'danger',
      isPromoted:true,
      isSoldout:true,
      highlightColor:'orange',
      headerSize:50,
      headerStyleObject:{
        color:'magenta',
        fontSize:'50px',
        padding:'20px'
      },
      shortHandStyleObject:{
        border:'1px solid black',
        color:'magenta',
        fontSize:'20px',
        fontStyle:'italic',
        padding:'20px'
      },
      num:50,
      display:true,
      showElement:true,
      tech:['Angular','React','Vue'],
      hero:[{name:'Bruce Wayne',tile:'Batman'},{name:'Tony Stark',tile:'IronMan'},{name:'Chris Hemsworth',tile:'Thor'}],
      actors:[
        {
          name:'Christian Bale',
          movies:['Batman','The prestige']
        },
        {
          name:'Di Caprio',
          movies:['Titanic','Inception']
        }
        ],
        info:{
          name:'Abhishek',
          company:'Tech',
          course:'Vue3'
        },
        conditionalNames:['Ram','Shyam','Mohan'],
        baseMultiplier:5,
        showPopup:false
    };
  },
  methods:{
    add(a){
      return function(b){
        return a+b
      }
    },
    mulByFive(num){
        return num*this.baseMultiplier
    },
    closePop(data){
      this.showPopup = false;
      console.log(`data from child ${data}`)
    }
  },
  provide(){
    return{
      username:this.name
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.underline{
  text-decoration:underline;
}
.promoted{
  font-style:italic;
}
.new{
  color:olivedrab;
}
.sold-out{
  color:red;
}

</style>
