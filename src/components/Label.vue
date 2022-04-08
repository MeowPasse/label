<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <el-button v-loading="loading" @click="designTemplate" type="warning">模板预览</el-button>
    <el-button v-loading="loading" @click="design" type="warning">模板设计</el-button>
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
        BARCODE: "1109242-00-C",
        QTY: "360 EA",
        WEIGHT:"650 KG",
        PRODUCT_ENG_NAME:"SUB ASY,INPUT,MACHINED,M ACRO2.0",
        ID:"3SEPV0003600011GT110924200C",
        SUPPLIER_ID:"186171",
        SUPPLIER_NAME:"Zhejiang Shuanghuan Driveline Co.Ltd",
        DATE:"18/61/2017",
        LOT_CODE:"20220317186171001A",
        LOT_CODE_QR:"P1109242-00-C:1T220317186171001A:17D"
      },
      value: `LODOP.PRINT_INITA(0,4,600,480,"");
LODOP.ADD_PRINT_TEXT(28,24,132,21,"MFG PART NUMBER:");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"FontSize",10);
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_RECT(23,22,156,50,0,1);
LODOP.ADD_PRINT_BARCODE(18,307,301,255,"QRCode","{{ID}}");
LODOP.ADD_PRINT_RECT(73,22,156,50,0,1);
LODOP.ADD_PRINT_TEXT(78,26,75,25,"QUANTITY:");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"FontSize",10);
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_TEXT(97,44,100,20,"{{QTY}}");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"FontSize",11);
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_TEXT(310,332,179,33,"{{BARCODE}}");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"FontSize",16);
LODOP.SET_PRINT_STYLEA(0,"Alignment",2);
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_RECT(23,178,130,50,0,1);
LODOP.ADD_PRINT_TEXT(29,183,85,15,"Origin:");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_TEXT(49,198,90,20,"CN-China");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"FontSize",12);
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_RECT(72,178,130,50,0,1);
LODOP.ADD_PRINT_RECT(122,22,286,80,0,1);
LODOP.ADD_PRINT_RECT(202,22,286,80,0,1);
LODOP.ADD_PRINT_RECT(282,22,286,70,0,1);
LODOP.ADD_PRINT_TEXT(79,181,100,10,"GROSS WEIGHT:");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_TEXT(97,193,95,15,"{{WEIGHT}}");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"FontSize",12);
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_TEXT(127,28,85,15,"PART NAME:");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"FontSize",10);
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_TEXT(143,23,271,15,"{{PRODUCT_ENG_NAME}}");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"FontSize",10);
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_TEXT(162,27,157,15,"CONTENT LABEL ID:");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"FontSize",10);
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_TEXT(180,25,274,15,"{{ID}}");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"FontSize",10);
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_TEXT(208,25,100,15,"SUPPLIER:");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"FontSize",10);
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_TEXT(212,98,135,15,"{{SUPPLIER_ID}}");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"FontSize",11);
LODOP.SET_PRINT_STYLEA(0,"Alignment",2);
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_TEXT(231,30,251,40,"{{SUPPLIER_NAME}}");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"FontSize",12);
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_TEXT(285,24,136,10,"PRINT DATE(UTC):");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_TEXT(285,142,100,10,"{{DATE}}");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_TEXT(300,24,100,10,"EXP DATE:");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_TEXT(314,23,100,10,"SERIAL NUM：");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_TEXT(331,23,70,10,"LOT CODE:");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_TEXT(331,96,148,15,"{{LOT_CODE}}");
LODOP.SET_PRINT_STYLEA(0,"FontName","黑体");
LODOP.SET_PRINT_STYLEA(0,"Bold",1);
LODOP.ADD_PRINT_BARCODE(284,240,110,82,"QRCode","{{LOT_CODE_QR}}");
`
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
     design() {
      let LODOP = getCLodop();
      let _self = this;
      let newValue = _self.value;
      eval(newValue)
      //LODOP.
      const tid = LODOP.PRINT_DESIGN();
      //LODOP.ADD_PRINT_DATA('ProgramData',self.value)
      console.log(tid);
      
      LODOP.On_Return = function(taskID, value) {
        _self.templateCode = value;
        console.log("taskID:"+taskID)
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
