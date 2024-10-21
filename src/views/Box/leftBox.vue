<template>
  <div class="box cards" @mouseenter="closeShow = true" @mouseleave="closeShow = false">
    <transition name="el-fade-in-linear">
      <close-one
        class="close"
        theme="filled"
        size="28"
        fill="#ffffff60"
        v-show="closeShow"
        @click=" function(){store.leftBoxOpenState = false ,store.leftBoxMsg = ''} "
      />
    </transition>

    <div class="content" style="background-color: #409EFF">

        <el-collapse v-model="activeNames" @change="handleChange"  v-for="(item, index) in userData" :key="item"  style="background-color: #409EFF">
<!--          <div v-for="(item, index) in userData" :key="item">-->

              <el-collapse-item :title="item.user" :name="index"  class="item cards"  >
                <div class="item cards">
                  {{item.msg}}
                </div>
              </el-collapse-item>
        </el-collapse>

    </div>
  </div>
</template>

<script setup>
import { CloseOne, SettingTwo } from "@icon-park/vue-next";
import siteLinks from "@/assets/siteLinks.json";
import { ref } from 'vue'


const activeNames = ref(['1'])
const handleChange = () => {
  // console.log(val)
}
const userData = [{
      "user":"测试用户",
      "msg":"留1111111111111111言",
      "time":"时间"
    },{
      "user":"测试用户2",
      "msg":"留言",
      "time":"时间"
    },{
      "user":"测试用户3",
      "msg":"留言",
      "time":"时间"
    }];
</script>

<style lang="scss" scoped>


.mh{
  background-color: #00000040;
  backdrop-filter: blur(10px);
}
//.item {
//   height: 100px;
//   width: 100%;
//   display: flex;
//   align-items: center;
//   flex-direction: row;
//   justify-content: center;
//   padding: 0 10px;
//   animation: fade 0.5s;
//
//  .cards {
//    border-radius: 6px;
//    background-color: #00000040;
//    backdrop-filter: blur(10px);
//    transform: scale(1);
//    transition:
//        backdrop-filter 0.3s,
//        transform 0.3s;
//  }
//
//}


.box {
  flex: 1 0 0%;
  margin-left: 0.75rem;
  height: 80%;
  max-width: 50%;
  position: relative;
  animation: fade 0.5s;

  &:hover {
    transform: scale(1);
  }

  .close,
  .setting {
    position: absolute;
    top: 14px;
    right: 14px;
    width: 28px;
    height: 28px;
    transition:
      transform 0.3s,
      opacity 0.3s;

    &:hover {
      transform: scale(1.2);
    }

    &:active {
      transform: scale(1);
    }
  }

  .setting {
    right: 56px;
  }

  .content {
    display: flex;
    flex-direction: column;
    padding: 30px;
    width: 100%;
    height: 100%;
  }
}
</style>
