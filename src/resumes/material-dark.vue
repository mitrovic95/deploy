<template>
<div class="resume">
  <div class="leftCol m_box">
    <div class="shadow"></div>
    <div class="heading" id="myselfpic">
    </div>
    <div class="section-headline" style="margin-top: 15px">
      {{ lang.contact }}
    </div>
    <div class="item">
      <div class="icon">
        <i class="material-icons">account_circle</i>
      </div>
      <div class="text">
        <ul>
          <li> {{ lang.born }} {{person.birth.day}}st {{person.birth.month}} {{person.birth.year}} {{ lang.bornIn }} {{person.birth.location}}</li>
        </ul>
      </div>
    </div>

    <div class="item">
      <div class="icon">
        <i class="material-icons">location_city</i>
      </div>
      <div class="text">
        <ul>
          <li>{{person.contact.street}}</li>
          <li>{{person.contact.city}}</li>
        </ul>
      </div>
    </div>

    <a :href="'tel:'+person.contact.phone">
      <div class="item">
        <div class="icon">
          <i class="material-icons">phone</i>
        </div>
        <div class="text">
          {{person.contact.phone}}
        </div>
      </div>
    </a>

    <a :href="'mailto:'+person.contact.email">
      <div class="item">
        <div class="icon">
          <i class="material-icons">email</i>
        </div>
        <div class="text">
          <span>{{person.contact.email}}</span>
        </div>
      </div>
    </a>

    <a v-if="person.contact.github" :href="'https://github.com/'+person.contact.github" target="_blank">
      <div class="item">
        <div class="icon">
          <i class="fa fa-github"></i>
        </div>
        <div class="text">
          <span>@{{person.contact.github}}</span>
          <span>github.com/{{person.contact.github}}</span>
        </div>
      </div>
    </a>

    <a v-if="person.contact.linkedin" :href="person.contact.linkedin" target="_blank">
      <div class="item">
        <div class="icon">
          <!-- <i class="zmdi zmdi-linkedin"></i> -->
          <img src="../../resume/linkedin.png" alt="" style="width: 25px;">
        </div>
        <div class="text">
          <span>{{person.contact.linkedin}}</span>
        </div>
      </div>
    </a>

    <a v-if="person.contact.website" :href="person.contact.website" target="_blank">
      <div class="item">
        <div class="icon">
          <i class="material-icons">language</i>
        </div>
        <div class="text">
          <span>{{person.contact.website}}</span>
        </div>
      </div>
    </a>

    <div class="item last">
      <div class="section-headline" style="margin-top: 15px">
        {{ lang.skills }}
      </div>
      <div class="skill" v-for="skill in person.skill" :key="skill.name">
        <div class="right">
          <span class="skill-name">{{skill.name}}&nbsp;</span>
          <div>
            <img :src="getImageUrl(skill.image)" class="skill-image" />
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="rightCol">
    <div class="title">
      <h2>{{person.name.first}} {{person.name.middle}} {{person.name.last}}</h2>
      <div>{{person.position}}</div>
    </div>
    <div class="section-headline">{{ lang.education }}</div>
      <div class="block" v-for="education in person.education" :key="education.image">
          <div>
            <img :src="getImageUrl(education.image)" class="education-icon" />
            {{education.degree}}
          </div>  
          <p class="info">
          {{education.description}}, {{education.timeperiod}}, {{education.location}}
          </p>
      </div>


<div class="section-headline">{{ lang.experience }}</div>
      <div class="block" v-for="experience in person.experience" :key="experience.project">
          <div>
            {{experience.project}}
          </div>  
          <p style="margin-top:5px;">
            {{experience.position}}
          </p>
          <p class="info">
            {{experience.description}}
          </p>
      </div>
    <!-- <div class="section-headline">{{ lang.experience }}</div>
      <div class="block">
        <p class="info-about">
        {{person.experience.company}}
        </p>
      </div> -->

    <div class="section-headline">{{ lang.hobbies }}</div>
      <div class="block" v-for="hobby in person.hobby" :key="hobby.image">
        <div class="center">
           <img :src="getImageUrl(hobby.image)" class="hobby-icon" />
           <span> {{hobby.description}}</span>          
        </div>
      </div> 
    </div>
  <div style="clear:both;"></div>
</div>
</template>

<script>
import Vue from 'vue';
import { getVueOptions } from './options';
let name = 'material-dark';

export default Vue.component(name, getVueOptions(name));
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
.resume {
  font-family:'Roboto' !important;
  background:#cccccc;
}
.education-icon {
  height: 18px;
}
 .center{
    text-align: left;
    padding-left: 165px;
    display: flex;
    span{
      padding-top: 4px;
      padding-left: 14px;
    }
  }
.hobby-icon { 
  height: 26px;
  padding-left: 10px;
  position: inherit;
}
a {
  cursor:pointer;
}
.description-personal {
  margin-left:20px;
  margin-top:20px;
  padding-right:40px;
  text-align:justify;
  font-family:Roboto;
}
.title {
  right:25px;
  padding-left:20px;
  // padding-top:20px;
  bottom:25px;
  margin-top: 15px;
  h2 {
    text-transform:uppercase;
    display:block;
    font-size:1.75em;
    -webkit-margin-before:1em;
    -webkit-margin-after:0;
    -webkit-margin-start:0;
    -webkit-margin-end:0;
    color:white;
    color:rgba(0,0,0,0.7);
    padding-top:0;
    margin-top:0;
    letter-spacing:10px;
    font-weight:400;
  }
  div {
    margin-top:-5px;
    margin-top:0;
    margin:0;
    margin-bottom: 15px;
    padding:0;
    line-height:15pt;
    font-weight:300;
    font-weight:500;
    letter-spacing:2px;
    letter-spacing:3px;
    color:white;
    color:#16151c;
    color:rgba(63,61,60,0.71);
    display:block;
    font-size:0.67em;
    font-size:11pt;
    -webkit-margin-before:0;
    -webkit-margin-start:0;
    -webkit-margin-end:0;
    padding-top:0;
    text-transform:uppercase;
    opacity:0.8;
  }
}
.section-headline {
  text-transform:uppercase;
  font-weight:500;
  letter-spacing:3px;
  font-size:10pt;
  opacity:0.8;
  margin-left:10px;
  margin-top:20px;
  color:#3f3d3c;
}
.c {
  clear:both;
}
li {
  margin:0;
  padding:0;
  list-style-type:none;
  padding-top:9px;
}
ul {
  margin:0;
  padding:0;
  list-style-type:none;
}
p {
  margin-top:0;
  margin-bottom:0;
  font-family:'Roboto', sans-serif;
  font-weight:300;
  font-size:10pt;
  line-height:17pt;
}
.m_box {
  box-shadow:0 2px 5px 0 rgba(0,0,0,0.16), 0 2px 10px 0 rgba(0,0,0,0.12);
}
.fa, .material-icons {
  display:inline-block;
  font-style:normal;
  font-weight:normal;
  line-height:1;
  -webkit-font-smoothing:antialiased;
  -moz-osx-font-smoothing:grayscale;
  font-size:26px;
}
h1, h3, h5, h6 {
  font-weight:400;
  margin:0;
}
h2 {
  font-weight:400;
  font-weight:500;
  margin:0;
  margin:0;
  font-size:22pt;
  line-height:37pt;
}
h4 {
  font-weight:400;
  margin:0;
  font-size:12pt;
  line-height:20pt;
  opacity:1;
}
.rightCol {
  width:60.5%;
  height:100%;
  float:right;
  display:flex;
  flex-direction:column;
    .hobby{
padding-right: 5px;
  height: 18px;
  &-description {
        display: table-cell;
        vertical-align: middle;
        width: 100px;
          margin-top:0;
  margin-bottom:0;
  font-family:'Roboto', sans-serif;
  font-weight:300;
  font-size:10pt;
  line-height:17pt;
      }
      &-image {
        position: absolute;
        height: 35px;
      }
  }
  .block {
    width:90%;
    position:relative;
    background-color:#ffffff;
    padding:10px 20px;
    margin-top:10px;
    margin-bottom:10px;
    display:inline-block;
    box-shadow:0 2px 5px 0 rgba(0,0,0,0.16), 0 2px 10px 0 rgba(0,0,0,0.12);
      .headline {
      font-weight:300;
      display:block;
      font-size:15px;
      color:rgba(0,0,0,0.870588);
    }
    .subheadline {
      color:rgba(0,0,0,0.541176);
      display:block;
      font-size:14px;
      font-weight:300;
    }
    .info {
      font-size:14px;
      color:rgba(0,0,0,0.870588);
      margin-bottom:0;
      padding-top:10px;
      .info-about{
        font-size:14px;
        color:rgba(0,0,0,0.870588);
        margin-bottom:0px;
      }
    }
    .icon {
      width:16%;
      float:left;
      margin-left:0;
      .fa, .material-icons {
        text-align:center;
        display:block;
        font-size:30pt;
      }
    }
    .content {
      width:80%;
      position:absolute;
      height:96%;
      left:17%;
      padding-right:3%;
      text-align:left;
      display:flex;
      flex-direction:column;
      .item {
        border-bottom:1px solid #bdbdbd;
        flex:1;
        width:97%;
        display:flex;
        justify-content:center;
        flex-direction:column;
        text-align:left;
        padding-top:0;
        span {
          color:#d8ab94;
          margin-top:0;
          font-size:10pt;
          line-height:16pt;
        }
        p {
          margin-top:5px;
        }
      }
      .item:last-of-type {
        border-bottom-style:none;
        border-bottom-style:none;
      }
    }
    div {
    display: flex;
  }
  }
}
.leftCol {
  width:38%;
  height:100%;
  float:left;
  padding:0;
  text-align:left;
  color:#ffffff;
  color:rgba(255,255,255,0.59);
  background-color:#16151c;
  overflow:hidden;
  display:block;
  .section-headline {
    color:rgba(255,255,255,0.54);
  }
  a {
    color:rgba(255,255,255,0.59);
    text-decoration:none;
  }
  .heading {
    background-color:white;
    background-repeat:no-repeat;
    background-size:cover;
    background-position:center;
    position:relative;
    width:100%;
    height:277px;
  }
  .item {
    width:100%;
    margin-top:13px;
    float:left;
    .fa, .material-icons {
      display:inherit;
      text-align:center;
    }
    .icon {
      width:20%;
      float:left;
      display: inherit;
      text-align: center;
    }
    .text {
      float:right;
      width:69%;
      padding-right:10%;
      padding-top:0;
      display:block;
      font-size:15px;
      font-weight:300;
      li {
        padding-top:0;
        display:block;
        font-size:15px;
        font-weight:300;
      }
    }
    span {
      font-weight:300;
    }
    .skill {
      clear:both;
      width:97%;
      padding-top:4px;
      div {
        position: relative;
        height: 40px;
      }
      &-name {
        display: table-cell;
        vertical-align: middle;
        width: 100px;
      }
      &-image {
        position: absolute;
        height: 35px;
      }
      .left {
        float:left;
        width:10%;
        padding-top:3px;
        i:nth-child(2) {
          float:left;
          padding-top:4px;
        }
      }
      .right {
        display: table;
        float:right;
        width:93%;
        .progress {
          float:left;
          position:relative;
          height:2px;
          display:block;
          width:95%;
          background-color:rgba(255,255,255,0.19);
          border-radius:2px;
          margin:0.5rem 0 1rem;
          overflow:visible;
          margin-bottom:10px;
          .determinate {
            background-color:#78909c;
            position:absolute;
            top:0;
            bottom:0;
            .fa, .material-icons {
              font-size:13px;
              position:absolute;
              top:-4px;
              right:-2px;
              margin-left:50%;
              color:white;
            }
          }
        }
      }
    }

    .skill:nth-child(3) {
      div {
        img {
          padding: 0 4px;
        }
      }
    }

    .skill:nth-child(5) {
      div {
        img {
          left: -26px;
          height: 50px;
          bottom: -4px;
        }
      }
    }

    .skill:nth-child(6) {
      div {
        img {
          left: 2px;
          height: 30px;
        }
      }
    }
  }
  .item.last .text {
    border-bottom-style:none;
    padding-bottom:0;
  }
}
#myselfpic {
  background-image:url('../../resume/id.png');
  color:black;
}
#githubIcon {
  width:25px;
  padding-left:17px;
}

.div.icon {
  width:25px;
  padding-left:17px;
}
</style>
