<template>
  <div class="hello">
      <pre>{{tmp}}</pre>
      <div class="row">
        <div class="col-sm-6">
          <div class="card" style="width: 20rem;"  v-for="(item,index) in posts">
            <div class="card-block">
              <h3 class="card-title">{{item.title}}</h3>
              <p class="card-text">NT$ {{item.id}}</p>
              <a href="#" class="btn btn-primary" @click="toggleCart(item,index)" 
                :class="{active:item.selected}"
              >已選購 </a>
            </div>
          </div>
        </div>
        <div class="col-sm-6">
          <div class="card" style="width: 20rem;">
            <div class="card-block">
              <h4 class="card-title">買了哪些東西</h4>
              <div v-for="(item,index) in posts" v-if="item.selected">
                <a href="#" class="btn btn-primary" @click="toggleCart(item,index)" 
                  >取消選購 </a>
                <p class="card-text">{{item.title}}</p>
                <p class="card-text">NT$ {{item.id}}</p>

              </div>
              <div>總價NT${{showPrice}}</div>
              </p>
            </div>
          </div>
          <div class="form-group">
            <label for="usr">Name:</label>
            <input type="text" class="form-control" id="usr" v-model="tmp.name">
          </div>
          <div class="form-group">
            <label for="usr">mail:</label>
            <input type="text" class="form-control" id="mail" v-model="tmp.mail">
          </div>
          <a href="#" class="btn btn-danger" @click="submit()" 
              >送出 </a>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      // msg: 'Welcome to Your Vue.js App'
      name:'',
      mail:'',
      profile:'',
      posts:[],
      tmp:{
        username:'',
        address:'',
        mail:'',
        cart:[]
      }
        
    }
  },
  
  methods:{
    getData(){
        // GET /someUrl
        let self = this;
        this.$http.get('http://localhost:3000/posts').then(response => {
          // get body data
          self.posts=response.body;
          console.log(response.body);
        }); 
    },
    toggleCart(item,i){
      console.log(item,i);
      let posts=this.posts
      let self =this
      self.$set(posts[i],'selected',!item.selected)
      console.log(self.posts)
      self.tmp.cart=posts.filter((product)=>{
        return product.selected
      })
      // console.log(self.tmp.cart);
    },
    submit(){
      let self = this 
      self.tmp.id=Math.random().toString(36).substring(7)
      self.$http.post('http://localhost:3000/posts',self.tmp).then(response => {
          // get body data
          // self.posts=response.body;
          console.log(response);
        }); 
    },
    
  },
  // 做預算綁定，不用觸發，只有資料有變動， 會馬上算出
  computed:{
    showPrice(){
      let cart = this.tmp.cart
      let self = this
      let total = 0
      cart.forEach((item)=>{
        total += item.id
      })
      return total
    },
  },
  mounted(){
    this.getData()
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
