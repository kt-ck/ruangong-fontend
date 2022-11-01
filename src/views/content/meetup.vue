<style scoped>
*{
    color:#1e293b;
}
.container{
    display: flex;
    flex-direction: column;
    width:100%;
    min-height:50vh;
}

.divider{
    height: 2px;
    background-color: black;
}

.gallery{
    width: 80%;
    padding:20px;
}
.gallery .date{
    font-size: 1.5rem;
    font-weight: bolder;
}

.cardList{
    display: flex;
    flex-direction: column;
}

.cardList .card{
    margin: 10px;
    padding: 20px;
    min-height: 5rem;
    border-bottom: 1px solid gray;
    display: flex;
    cursor: pointer;
}

.cardList .card img{
    width: 8rem;
}

.cardList .card .main{
    width: 100%;
    margin-left: -4rem;
    display: flow-root;
    position: relative;
}

.cardList .card .main .time{
    margin-left:4rem;
    color: rgb(63 98 18);
    font-size: 1.3rem;
    font-weight: bold;
}

.cardList .card .main .suggest{
    position: absolute;
    right:0;
    top:0;
    color: #22c55e;
    font-size: 1.5rem;
    font-weight: bold;
}

.cardList .card .main .title{
    margin-left:4rem;
    font-weight: bold;
    color: rgb(28 25 23);
    font-size: 1.3rem;
}

.cardList .card .main .sub-title{
    margin-left:4rem;
    color: rgb(87 83 78);
    font-size: 1rem;
}

.cardList .card .main .subscribe{
    margin-left:4rem;
    color: rgb(168 162 158);
    font-size: 1rem;
    margin-top:1rem;
    line-height: 1.5rem;
    white-space: normal;
    letter-spacing: 0.1rem;
}



</style>
<template>
  <Content class="IonaContent">
    <div class="container">
       <section v-for="item in activityList" :key="item.id" class="gallery">
            <p class="date">{{item.date}}</p>
            <div class="divider"></div>
            <div class="cardList">
                <div v-for="act in item.activity" :key="act.id" class="card" @click="gotoAct(act.id)">
                    <img :src="act['img-url']" :alt="act['img-alt']"/>
                    <div class="main">
                        <p class="time">{{act.time}}</p>
                        <span class="suggest">Suggest</span>
                        <p class="title">{{act.title}}</p>
                        <p class="sub-title">{{act["sub-title"]}}</p>
                        <p class="subscribe">{{act["subscribe"]}} attendee</p>
                    </div>
                </div>
            </div>  
       </section>
    </div>
  </Content>
</template>
<script>
export default {
  data() {
    return {
      activityList: [{
        "id":"1",
        "date": "2022/10/11 星期三",
        "activity":[
            {
                "id":"1-1",
                "time":"18:00PM",
                "title":"testttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttttt",
                "img-alt":"img1",
                "img-url":"",
                "sub-title":"sub-title testttttttttt ttttttttttttttttttttttttttttttttt tttttttttttttttttttttttttttt ttttttttttttttt",
                "subscribe": 4
            },
            {
                "id":"1-2",
                "time":"18:00PM",
                "title":"test",
                "img-alt":"img1",
                "img-url":"",
                "sub-title":"sub-title test",
                "subscribe": 4
            }
        ]

      },{
        "id":"2",
        "date": "2022/10/11 星期三",
        "activity":[
            {
                "id":"2-1",
                "time":"18:00PM",
                "title":"test",
                "img-alt":"img1",
                "img-url":"",
                "sub-title":"sub-title test",
                "subscribe": 4
            },
            {
                "id":"2-2",
                "time":"18:00PM",
                "title":"test",
                "img-alt":"img1",
                "img-url":"",
                "sub-title":"sub-title test",
                "subscribe": 4
            }
        ]

      }]
    };
  },
  created: function() {
  },
  methods: {
    gotoAct(activityId){
        this.$router.push({
            name : "activity",
            params:{
                activityId
            }
        })
    }
  }
};
</script>