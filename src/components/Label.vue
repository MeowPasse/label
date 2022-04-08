<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <el-button v-loading="loading" @click="designTemplate" type="warning">模板设计</el-button>
    <el-button v-loading="loading" @click="handlePrint" type="warning">模板打印</el-button>

  </div>
</template>

<script>

export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      context: {
        barcode1: "1109242-00-C",
        QTY: "360 EA"
      },
      value: `LODOP.PRINT_INITA(0,4,300,180,"");
              LODOP.ADD_PRINT_TEXT(23,22,157,26,"MFG PART NUMBER:");
              LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
              LODOP.SET_PRINT_STYLEA(0,"FontSize",11);
              LODOP.SET_PRINT_STYLEA(0,"Bold",1);
              LODOP.ADD_PRINT_RECT(23,22,156,35,0,1);
              LODOP.ADD_PRINT_BARCODE(22,181,301,70,"QRCode","{{barcode1}}");
              LODOP.ADD_PRINT_RECT(58,22,156,60,0,1);
              LODOP.ADD_PRINT_TEXT(58,23,75,25,"QUANTITY:");
              LODOP.ADD_PRINT_TEXT(89,29,100,20,"{{QTY}}");
              LODOP.ADD_PRINT_TEXT(99,179,100,20,"{{barcode1}}");
              LODOP.SET_PRINT_STYLEA(0,"FontSize",11);
              LODOP.SET_PRINT_STYLEA(0,"Bold",1);`
    }
  },
  created() {
    var head =
      document.head ||
      document.getElementsByTagName("head")[0] ||
      document.documentElement;
    var oscript = document.createElement("script");
    oscript.src = "http://localhost:8000/CLodopfuncs.js?priority=1";
    head.insertBefore(oscript, head.firstChild);
  },
  methods:{
    designTemplate() {
      let LODOP = getCLodop();
      let _self = this;
      let newValue = _self.value;
      //LODOP.
      for (var k in _self.context) {
        console.log(k+"->"+_self.context[k])
        newValue = newValue.replaceAll("{{"+k+"}}",_self.context[k])
      }
      console.log(newValue)

      eval(newValue)
      const tid = LODOP.PRINT_DESIGN();
      //LODOP.ADD_PRINT_DATA('ProgramData',self.value)
      console.log(tid);
      
      LODOP.On_Return = function(taskID, value) {
        _self.templateCode = value;
        console.log("origin value:"+_self.value)
        console.log("value:"+value)
      };
    },
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
