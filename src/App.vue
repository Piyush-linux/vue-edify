<template>
    <!-- sidebar -->
    <section class="section">
      <Alert :alert="alert"/>
        <div class="container">
            <!-- notification -->
            <!-- editor -->
            <div class="columns " id="editor">
                <!-- sidebar -->
                <Sidebar  :dark="dark" :toggleMode="toggleMode" :txtClear="txtClear" :txtCpy="txtCpy" :txtUpp="txtUpp" />
                <!-- editor -->
                <div class="column" :class="{ txtDark : dark, txtLight: !dark }" >
                    <div class="field">
                        <div class="control">
                            <textarea class="textarea has-fixed-size" placeholder="e.g. Hello world" rows="18" v-model="txt"></textarea>
                        </div>
                    </div>
                    <div class="field has-addons">
                        <div class="control">
                            <div class="button is-link is-small">
                                char : {{ txt.length }}
                            </div>
                        </div>
                        <div class="control">
                            <div class="button is-small">
                                 words : {{ txt.split(" ").length }}  
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>
<script>
// import Textarae from './components/Textarea.vue'
import Sidebar from './components/Sidebar.vue'
import Alert from './components/Alert.vue'
import "./assets/bulma.min.css"

export default {
    name: 'App',
    components: {
        Sidebar,
        Alert
    },
    data() {
        return {
            mode: "dark",
            txt:"",
            dark: true,
            alert: {mssAlert:null, showAlert:false}
        }
    },
    methods: {
        toggleMode() {
            if (this.mode == "dark") {
                this.mode = "light"
                this.dark=false
                this.notify("Toggle dark mode")
                console.log('toggle !')

            } else {
                this.mode = "dark"
                this.dark=true
            }
        },
         txtClear(){
            this.txt=""
            this.notify("New Screen")
        },
        txtUpp(){
            this.txt = this.txt.toUpperCase()
            this.notify("Text Converted To Upper Case")
        },
        txtLow(){
            this.txt = this.txt.toLowerCase()
            this.notify("Text Converted To Lower Case")
        },
        txtCpy(){
            let txtArea = document.querySelector(".textarea")
            txtArea.select()
            navigator.clipboard.writeText(txtArea.value)
            this.notify("Text Copied To Clipboard")
        },
        notify(mess){
            // not.style.display = 'block'
            console.log(this.alert)
            this.alert.mssAlert = mess
            this.alert.showAlert = true
            setTimeout(()=>{
            this.alert.showAlert = false
                // not.style.display = 'none'
            },2000)
        }
       
    }
}
</script>
<style>
.iconify {
    font-size: 3rem;
}
.cen{
    display: flex;
    align-items: center;
    justify-content: center;
}
.notification{
    position: fixed;
    z-index: 2;
    /*width: 100%;*/
    font-weight: bold;
    /*display: none;*/
    transition: 1s;
    border-radius: 10px;
    opacity: .7;
}
.button{
  outline: none;
  border: none;
}
.button:hover{
box-shadow: 6px 5px 26px 0px rgba(0,0,0,0.74);
-webkit-box-shadow: 6px 5px 26px 0px rgba(0,0,0,0.74);
-moz-box-shadow: 6px 5px 26px 0px rgba(0,0,0,0.74);
}
.button:active{
  box-shadow: none;
}
#editor {
    width: 100%;
    height: 90vh;
}

/*sidebar*/
.sidebarDark {
    background-color: #1abc9c;
}
.sidebarDark .button{
  color: #1abc9c;
}

.sidebarLight{
  background-color: #2c3e50; 
}
.sidebarLight .button{
  color: #2c3e50;
  background-color: #1abc9c;
}

/* txt */
.textarea{
    background: transparent;
    border: none;
    font-family: monospace;
    font-size: 1.1rem;
    font-weight: bold;
}
.textarea:focus{
    outline: none;
}
.txtLight {
  background-color: #ecf0f1;
}
.txtLight .icon{
  color : #16a085;
}
.txtDark{
  background-color: #34495e;
}
.txtDark .textarea {
    color: #1abc9c;
}

.textarea:hover {
    border: none;
    outline: none;
}

.btn {
    margin-top: 1rem;
}
</style>