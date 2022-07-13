<template>
  <div class="hello">
    <h1>TextToEncrypt</h1>
    <input v-model="inputText" placeholder="Enter a string" /> <br /><br/>
    <button @click="encrypt()">Encrypt2</button>
    
    <h1>{{resultEncrypt}}</h1> 
  </div>
</template>

<script>

export default {  name: "aes-page",
  data: () => ({
     inputText:"",
     resultEncrypt: "",
    }),


    methods: {
        encrypt(){
        
          let key = this.$CryptoJS.enc.Utf8.parse('TRIMULFT1V09O17L1019E2991V09MAPI');
          let iv = this.$CryptoJS.enc.Utf8.parse('2022E2991V09O17L');

          let srcs = this.$CryptoJS.enc.Utf8.parse(this.inputText)
          var encrypted = this.$CryptoJS.AES.encrypt(srcs, key, 
            {
              iv: iv,
              mode: this.$CryptoJS.mode.CBC,
              padding: this.$CryptoJS.pad.Pkcs7
            })
            //console.log("-=-=-=-", encrypted.ciphertext)
            this.resultEncrypt = this.$CryptoJS.enc.Base64.stringify(encrypted.ciphertext);
        }
    },

   
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
