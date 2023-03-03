
<template>
  
  <!-- mustach symbol is used to get values form data  -->
  <h1>hello {{ name }}</h1>
  <!-- v-text is the directive that is also used for getting values from data  -->
  <!-- The only issues is it replaces the complete block or tag values with the data -->
  <div v-text=news></div>
  
  <div v-text=bold_val></div>
  <!-- v-html is used to render html  -->
  <div v-html=bold_val></div>
  <!-- v-bind  is used for binding attributes-->
  <div v-bind:Id="headingid">V-bind use case</div>
  <button :disabled="isdisabled">USE CASE button FOR V-BIND</button>

  <!-- v-bind with classes -->
  <h3 :class="issoldout ? 'sold_out':'new'">vbind for classes</h3>
  <h3 :class="ispromoted && 'promoted'">vbind for classes</h3>
  <h3 :class="['new','promoted']">vbind for classes</h3>
  <h3 :class="ispromoted && 'promoted',issoldout ? 'sold_out':'new'">vbind for classes with conditions</h3>
  
  <h3 class="new">in tradiontal html we can only play with class per tag</h3>

  <h3 :class="{
    new_background:ispromoted,
    new:!issoldout,
    sold_out:issoldout
  }">vbind for classes with object conditions</h3>

  <!-- binding style -->
  <h3 :style="{
    color:hightlight_color,

  }">inline css with v-bind</h3>

  <!-- ##Methods##-->

  <!-- event handling -->
  <div>   
     <h2>{{ name }}</h2>
    <button @click="name='bella'">change name</button>
    <button @click="change_name($event) , increment(1,$event)">change name1 with increment</button>
    <h2>{{count}}</h2>
    <button @click="increment(1,$event)">increment value</button>
  </div>
  
  <!-- Form Handling -->
  <div>
    <pre>
      {{ JSON.stringify(form_handling,null,2) }}
    </pre>
    <form>
      <div>
        <label for="name">Name</label>
        <input type="text" id="name" v-model='form_handling.name'/>
      </div>
    
      <div>
        <label for="profile_id">Profile_Summary</label>
        <textarea type="text" id="profile_id" v-model='form_handling.Profile_Summary'/>
      </div>
      <div>
        <label for="country">Country</label>
        <select id="country" v-model="form_handling.country">
          <option value="">select country</option>
          <option value="india">India</option>
          <option value="america">America</option>
          <option value="austrelia">Austrelia</option>
          <option value="us">US</option>
        </select>
        
      </div>
    </form>
    <!-- http get request -->
    <br>
  <div >
<!-- gethttp -->
  <postlist/>
  <br>
  <br>
  <!-- posthttp -->
  <createcompany/>

  </div>
  
    
  </div>


</template>

<script>

import postlist from './components/postlist.vue'
import createcompany from './components/createcompany.vue'

export default{
  name:"App",
  data() {
    return {
      name: "vaishnavi",
      news: "The Sports Quiz organized jointly by The Hindu Future India Club (FIC) and Odisha Mining Corporation (OMC) on Wednesday witnessed 300 students from Sambalpur region actively participating and exhibiting their intellect in the realm of sports.",
      bold_val:'<u><i>v-html use case</i></u>',
      headingid: "Heading",
      isdisabled: true,
      issoldout: true,
      ispromoted:true,
      hightlight_color:'orange',
      count:0,
      form_handling:{
        name:'',
        Profile_Summary:'',
        country:''
      }  
    }
  },
  components:{
      postlist,
      createcompany
    },
  methods:{
    increment(num,event){
      console.log("Event",event)
      return this.count=this.count+num
      // return this.count+=num
    },
    change_name(event){
    this.name="Bella"
    console.log("Event",event)
  }
  },
  
}

</script>

<style >
.promoted{
  background-color: white;
  color:black;
 
}
.new_background{
  background-color: blanchedalmond;
}

.new{
  color: green;
}

.sold_out{
  color:red;
}


</style>
