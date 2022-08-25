<template>
<div>
      <textarea  v-model="md" name="md" id="" cols="30" rows="10"></textarea>
      <button @click="getHtml">Enter</button>
      <textarea  v-model="html" name="html" id="" cols="30" rows="10"></textarea>
</div>
      
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      md: '',
      html: ''
    }
  },
  methods: {
     
      getHead() {
         

        let str =  this.md.split('')
         

        let head = ''

         for (let i = 0; i <= 6; i++) {
                if (str[i] != '#') {
                    let re = /#{1,4}/g
                    head += `<h${i}>${this.md.replace(re, '')}</h${i}>`
                    break
                }  
         }
              this.html = head
          
        

            
},


 getPara() {
  if (!this.md.includes('#') && !this.md.includes('-')) {
        this.html = `<p>${this.md}</p>`
  }
    
 
},




 getList() {
         

        let str = this.md.split('\n')
        let list = '<ul>'
        for (let item of str) {
            if (item === '') continue
            list += `<li>${item.replace('-', '')}</li>`
        }
        list += '</ul>'
        this.html = list
        console.log(str)
        console.log(list)
        
      },
        getHtml()  {
          if (this.md.match(/[a-zA-Z1-9]/))  this.getPara()
         
         
          if (this.md.match(/#{1,4}/g)) this.getHead()
          
         if (this.md.startsWith('-') && this.md.endsWith('\n')) this.getList()
         }
        
}

  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
