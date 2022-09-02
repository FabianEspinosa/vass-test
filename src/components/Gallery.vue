<template>
    <div>
        <div class="bar1">
                <img class="barLogo" src="../assets/sneak.png"> 
                <b-button class="barButton" type="is-ghost">All</b-button>           
                <b-button class="barButton" type="is-ghost">Branding</b-button>           
                <b-button class="barButton" type="is-ghost">Web</b-button>           
                <b-button class="barButton" type="is-ghost">Photography</b-button>           
                <b-button class="barButton" type="is-ghost">App</b-button>
                <b-icon class="barIcon" icon="search" pack="fas" size="is-medium"></b-icon>
        </div>
        <div class="bar2">
            <span class="barTitle">
                EXPLORE BEYOND HORIZON
            </span>
            <span class="barSubTitle">
                Magna mundi referrentur quo, no rebum dignissim qui.<br>
                Per quodsi accusata id, agam labores.
            </span>
            <b-button class="barButton">VIEW OUR WORK</b-button>
        </div>
        <div class="barIcons">
                    <b-icon class="barIcon" icon="th-large" pack="fas" size="is-medium"></b-icon>
                    <b-icon class="barIcon" icon="equals" pack="fas" size="is-medium"></b-icon>
        </div> 
        <div class="bar3">                
                <b-button class="barButton" type="is-ghost">All</b-button>           
                <b-button class="barButton" type="is-ghost">Branding</b-button>           
                <b-button class="barButton" type="is-ghost">Web</b-button>           
                <b-button class="barButton" type="is-ghost">Photography</b-button>           
                <b-button class="barButton" type="is-ghost">App</b-button>          
        </div>
        <div class="filterButtons"> 
                <b-button :class="{active : pairActive}" class="filterButton" @click="tooglePair">Pares</b-button>
                <b-button :class="{active : allActive}" class="filterButton" @click="activeAll">todos</b-button>
                <b-button :class="{active : oddActive}" class="filterButton" @click="toogleOdd">Impares</b-button>
        </div>
        <div class="gallery">     
            <div class="gallery-panel"
                v-for="photo in data"
                :key="photo.id">
                <img :src="photo.url" style="width:100%">{{photo.id}}
            </div>
        </div>
        <div class="foots">
            <b-button class="barButton">Show Me More</b-button>
            <span class="barSubTitle">
                © 2016 - <span style="color: #FC758C">Sneak</span> All Right Reserved
            </span>
            <div class="networks">
                <img class="barLogo" src="../assets/networks.png">
            </div>
        </div> 
    </div> 
</template>

<script>
export default {
  name: 'Gallery',
  data() {
    return {
        pairActive:false,
        oddActive:false,
        allActive:true,
        dataComplete: null
    }
  },
  props: ['data'],
  mounted() {
    this.dataComplete = this.data;
  },
  methods: {
    tooglePair: function () {        
        this.pairActive = !this.pairActive
    },
    toogleOdd: function () {        
        this.oddActive = !this.oddActive
    }, 
    activeAll: function () {        
        this.oddActive = false
        this.pairActive = false
        this.allActive = true
    }  
  },
  watch:{
    pairActive: function() {
        this.data = this.dataComplete;
        if (this.pairActive) {
            this.allActive = false           
            this.data = this.data.filter(data => data.id % 2 == 0)
        }
        if (!this.pairActive && !this.oddActive) {
            this.allActive = true
        }    
    },
    oddActive: function() {
        this.data = this.dataComplete;
        if (this.oddActive) {
            this.allActive = false            
            this.data = this.data.filter(data => data.id % 2 != 0)
        }
        if (!this.pairActive && !this.oddActive) {
            this.allActive = true
        }        
    }
  }

}
</script>
<style lang="scss">
    .bar1 {
        display: flex;
        width: 100%;
        justify-content: flex-end;
        padding:30px 100px 30px 10px;
        .barLogo {
            margin-right: auto;
            margin-left: 125px;
        } 
        .barButton {
            margin-left: 10px;
            letter-spacing: 3px;
            font-size: 14px;
            color: #838383!important;
            border-radius: 0%;
            &:hover{
                background-color: #FF5672;
            }
        }
        .barIcon {
            margin-top: 4px;
            margin-left: 10px;
            color: #FF5672;
            margin-right: 55px;
        }
    }
    .bar2 {
        background-color: #FC758C;
        height: 800px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin-bottom: 50px;
        .barTitle{
            color: #fff;
            font-size: 45px;
            letter-spacing: 5px;
            margin-bottom: 25px;
        }
        .barSubTitle{
            color:#fff;
            font-size: 18px;
            letter-spacing: 3px;            
            text-align: center;
            margin-bottom: 50px;
        }
        .barButton {
            border-radius: 0%;
            color: #FC758C;
            font-weight: bold;
            letter-spacing: 2px;
            font-size: 10px;
            height: 40px;
            span {
                padding: 10px 10px 10px 10px;
            }
        }
    }
    .barIcons {
        display: flex;
        justify-content: center;
        color :#FF5672;
        .barIcon {
            margin-right: 20px;
        }
    }
    .bar3 {
        display: flex;
        width: 100%;
        justify-content: center;
        padding:30px 100px 30px 10px;       
        .barButton {
            margin-left: 10px;
            letter-spacing: 3px;
            font-size: 14px;
            color: #838383!important;
            border-radius: 0%;
            &:hover{
                background-color: #FF5672;
            }
        }        
    }
    .gallery {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(20rem, 1fr));
      grid-gap: 1rem;
      max-width: 80rem;
      margin: 5rem auto;
      padding: 0 5rem;
    }  
    .gallery-panel img {
      width: 100%;
      height: 22vw;
      object-fit: cover;      
    }
    .filterButtons {
        display: flex;
        justify-content: center;
        .filterButton {
            width: 90.31px;
            border-radius: 0%;
        }
        .active {
            background-color: #FC758C;
            color: #fff!important;
        }
    }
    .foots {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 250px;
        flex-direction: column;     
        .barButton {
            border-radius: 0%;
            background-color: #FC758C;
            color: #fff;            
            letter-spacing: 2px;
            font-size: 13px;
            height: 40px;
            margin-bottom: 50px;       
            span {
                padding: 10px 10px 10px 10px;
            }
        }
        .barSubTitle {
            color: #C2CFD7;
            letter-spacing: 3px;
            margin-bottom: 30px;
        }
    }
    .button:focus, .button.is-focused {
        border-color: #fff!important;   
    }
</style>
