<template lang="html">
  <div class="container__portfolio pl-2 pr-2" >
    <div class="row">
      <ProjectFirst />
      <ProjectSecond />
      <ProjectThree />
      <ProjectFourth />
      <ProjectFive />
      <ProjectSix />

    </div>
  </div>
</template>

<script>
import ProjectFive from './projects/ProjectFive'
import ProjectFourth from './projects/ProjectFourth'
import ProjectThree from './projects/ProjectThree'
import ProjectFirst from './projects/ProjectFirst'
import ProjectSecond from './projects/ProjectSecond'
import ProjectSix from './projects/ProjectSix'
export default {
  name: 'portfolio',
  components: {
    ProjectFive,
    ProjectFourth,
    ProjectThree,
    ProjectFirst,
    ProjectSecond,
    ProjectSix,
  },
  data () {
    return {
    }
  },
}
</script>

<style lang="css">
.container__portfolio {
  padding-top: 90px;
  padding-bottom: 90px;
}
.mw-100 {
  max-width: 100%;
}
.portfolio_img{
  position: relative;
  transition: all .4s ease;
  margin: 0;
  padding: 0;
}
.portfolio_img::before{
  content: '';
  background: -webkit-linear-gradient(50deg,#ff6ec4,#7873f5)!important;
  background: -o-linear-gradient(50deg,#ff6ec4,#7873f5)!important;
  background: linear-gradient(40deg,#ff6ec4,#7873f5)!important;
  position: absolute;
  width: 100%;
  height: 0;
  opacity: 0;
  transition: all .7s ease-in-out;
}
.portfolio_img:hover::before {
  opacity: 1;
  height: 100%;
}
.description__block {
  position: absolute;
  width: 100%;
  height: 0;
  z-index: 555;
  display: block;
  top: 0;
  opacity: 0;
  transition: all 1.2s ease-in-out;
  text-align: center;
  display: flex;
  flex-flow: column;
  justify-content: center;
}
.portfolio_img:hover .description__block{
  height: 100%;
  opacity: 1;
}
.down_line {
  width: 45px;
  background: #fff;
  display: block;
  margin: 0 auto;
  height: 1px;
}
.modal__container {
  width: 100%;
  position: absolute;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  z-index: 777;
  display: block;
  top:0;
  left: 0;
  display: flex;
  justify-content: center;
}
.--inner__modal {
  z-index: 999;
  height: auto;
  overflow-y: scroll;
  top: 60px;
  position: absolute;
  display: block;
  margin: 0 auto;


}
.list_comments {
  list-style-type: none !important;
  display: flex;
  flex-flow: column-reverse;
}
.close_container {
  position: absolute;
  right: 0px;
  top: 5px;
  z-index: 999;
  width: 40px;
  height: 40px;
}
.far, .fas {
  transition: all .4s ease;
  color: #666;
}
.far:hover, .fas:hover {
  color: #000;
}
.fa-times-circle {
  z-index: 9999;
  color: #000;
}
.fa-times-circle:hover {
  color: #fff;
}
@media screen and (max-width: 768px ) {
  .far:hover, .fas:hover {
    color: #666;

  }
  .fa-times-circle:hover {
    color: #666;


  }
}
.scrollbar-primary::-webkit-scrollbar {
width: 12px;
background-color: #F5F5F5; }

.scrollbar-primary::-webkit-scrollbar-thumb {
border-radius: 10px;
-webkit-box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.1);
background-color: #4285F4; }
.scrollbar-default::-webkit-scrollbar {
width: 12px;
background-color: #F5F5F5; }

.scrollbar-default::-webkit-scrollbar-thumb {
border-radius: 10px;
-webkit-box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.1);
background-color: #2BBBAD; }
.scrollbar-secondary::-webkit-scrollbar-track {
-webkit-box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.1);
background-color: #F5F5F5;
border-radius: 10px; }

.scrollbar-secondary::-webkit-scrollbar {
width: 12px;
background-color: #F5F5F5; }

.scrollbar-secondary::-webkit-scrollbar-thumb {
border-radius: 10px;
-webkit-box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.1);
background-color: #aa66cc; }
</style>
