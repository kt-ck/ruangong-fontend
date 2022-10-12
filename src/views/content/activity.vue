<style scoped>
*{
    background-color: white;
    color:#1e293b;
}
.container{
    width:100%;
    min-height:60vh;
    height: 80vh;
    display: flow-root;
}

.header{
    width:100%;
    position: sticky;
    top: 0px;
    padding: 1rem 2rem;
    border-bottom: 1px solid #ccc;
}
.header div{
    margin-top: 1rem;
    display: flex;
    align-items: center;
}
.header div img{
    width: 3rem;
    height: 3rem;
    border-radius: 50%;
}

.header div p{
    margin-left: 1rem;
    display: block;
    font-size: 1rem;
}

.content{
    width: 100%;
}

.main{
    width: 60%;
    padding: 2rem 5rem;
    display: inline-block;
}

.main .activity-img{
    width: 100%;
}

.main>p{
    font-size: 1.5rem;
    font-weight: bolder;
    margin: 1rem 0;
}

.side{
    min-width: 10rem;
    max-width:20rem;
    display: inline-block;
    position: sticky;
    top:30vh;
}
.detail{
    width: 100%;
    white-space: normal;
    line-height: 1.5rem;
    text-indent: 1rem;
    letter-spacing: 0.2rem;
}

.attendee-list{
    display: flex;
    padding-bottom: 10rem;
}

.personal-card{
    height: 10rem;
    padding: 1rem;
    width: 7rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    border: 1px solid #57534e;
    margin-left: 1rem;
    border-radius: 0.3rem;
}

.personal-card>img{
    width: 3rem;
    height: 3rem;
    border-radius: 50%;
}
.personal-card>p{
    font-size: 1rem;
    font-weight: bold;
    color:#1e293b;
}

.personal-card>span{
    color:#94a3b8;
}

.group{
    border:1px solid #57534e;
    border-radius: 0.3rem;
    padding: 2rem;
    display: flex;
    align-content: center;
}

.group>img{
    width: 3rem;
    height: 3rem;
    border-radius: 50%;
    margin-right:1rem;
}

.group>div>p{
    color:#94a3b8;
    letter-spacing: 0.1rem;
}

.address{
    margin-top: 1rem;
    border:1px solid #57534e;
    border-radius: 0.3rem;
    padding: 2rem;
    white-space: normal;
}

.address .row{
    display: flex;
    margin-bottom: 1rem;
}
.address .row>span img{
    display: block;
    width: 2rem;
}

.address .row>p{
    margin-left: 1rem;
    line-height: 1.5rem;
    letter-spacing: 0.1rem;
}

button.attend{
    width: 100%;
    color: white;
    background-color: #fb7185;
    border: none;
    padding: 0.8rem;
    margin-top: 1rem;
    font-size: 1.3rem;
    font-weight: bold;
    border-radius: 0.3rem;
    cursor: pointer;
}

button.attend:hover{
    transform: scale(0.99)
}



</style>
<template>
  <Content>
    <div class="container">
        <section class="header"> 
            <h1>{{activity.title}}</h1>
            <div>
            <img :src="activity.avatar" alt="avater" />
            <p><span>HOSTED BY</span><br/><b>{{activity.host}}</b></p>
            </div>
        </section>
        <section class="content">
            <div class="main">
                <div class="activity-img">
                    <img :src="activity['img-url']" :alt="activity['img-alt']"/>
                </div>
                <p>Detail</p>
                <div class="detail">
                    {{activity.details}}
                </div>
                <p>Attendee({{activity.attendeeNum}})</p>
                <div class="attendee-list">
                    
                    <div v-for="guy in activity.attendeeList" :key="guy.id">
                        <div class="personal-card">
                            <img :src="guy.avatar" :alt="`avater image`" />
                            <p>{{guy.name}}</p>
                            <span>{{guy.position}}</span>
                        </div>
                    </div>
                    
                </div>
            </div>
            <div class="side">
                <div class="group">
                    <img :src="activity.group['img-url']" alt="group image" />
                    <div>
                        <h3>{{activity.group.name}}</h3>
                        <p>{{activity.group.type}}</p>
                    </div>
                </div>
                <div class="address">
                    <div class="row">
                        <span>
                            <img src="../../assets/icons/clock-fill.svg" />
                        </span>
                        <p>{{activity.time}}</p>
                    </div>
                    <div class="row">
                        <span>
                            <img src="../../assets/icons/location-fill.svg"/>
                        </span>
                        <p>{{activity.address}}</p>
                    </div>
                </div>
                <div>
                    <button class="attend">Attend</button>
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
      activityId: "",
      userId: "",
      activity: {
        title: "中韓語交流會수요일 모임",
        host: "kt-ck",
        avatar:"",
        group: {
           name: "LEIT",
           "img-url":"",
           "type":"public group"
        },
        "img-alt": "image",
        "img-url": "",
        time: "Wednesday, October 12, 2022 at 7:00 PM to Wednesday, October 12, 2022 at 11:00 PM GMT+8 Every week on Wednesday",
        address: "玉門街一號 maji square · Taipei",
        details: "想要 #練習講韓語 或是 #認識韓國朋友，都歡迎來參加想要 #練習講韓語 或是 #認識韓國朋友，都歡迎來參加我們聚會。就算不會說韓語也沒關係想想要 #練習講韓語 或是 #認識韓國朋友，都歡迎來參加我們聚會。就算不會說韓語也沒關係想想要 #練習講韓語 或是 #認識韓國朋友，都歡迎來參加我們聚會。就算不會說韓語也沒關係想我們聚會。就算不會說韓語也沒關係想要 #練習講韓語 或是 #認識韓國朋友，\n都歡迎來參加我們聚會。就算不會說韓語也沒關係想要 #練習講韓語 或是 #認識韓國朋友，都歡迎來參加我們聚會。就算不會說韓語也沒關係想要 #練習講韓語 或是 #認識韓國朋友，都歡迎來參加我們聚會。就算不會說韓語也沒關係",
        attendeeNum:24,
        attendeeList: [{
            userId: 2,
            avatar: "",
            name: "ck-kt",
            position: "manager" 
        },{
            userId: 3,
            avatar: "",
            name: "ck-kt",
            position: "manager" 
        }],

      }
    };
  },
  mounted: function(){
    this.activityId = this.$route.params.activityId
    this.userId = this.$store.state.userData.id
  },
  created: function() {
  },
  methods: {
    
  }
};
</script>