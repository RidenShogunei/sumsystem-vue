<template>
  <el-container direction="vertical">
    <el-header class="title">
      <div :style="{ color: 'white' }">总系统</div>
    </el-header>
    <el-container>
      <div class="aside">
        <el-aside width="250px" class="aside">
          <el-menu :default-active="activeLang" class="el-menu-demo" mode="vertical"
            style="height: 100%; overflow-y: auto">
            <el-menu-item index="vue">Vue</el-menu-item>
            <el-menu-item index="react">React</el-menu-item>
          </el-menu>
        </el-aside>
      </div>
      <el-container>
        <el-main>
          <el-row :gutter="20">
            <el-col :xs="24" :sm="12" :md="8" :lg="6" :xl="6" v-for="system in systems" :key="system.index">
              <el-card :body-style="{ padding: '0px' }" class="box-card" @click="open(system.url)">
                <div style="padding: 14px;">
                  {{ system.name }}
                </div>
                <div>
                  {{ system.description }}
                </div>
              </el-card>
            </el-col>
          </el-row>
        </el-main>
        <el-footer>
          <div class="footer">
            <a href="https://beian.miit.gov.cn" target="_blank" rel="noopener noreferrer" style="color:white;">{{ ICP
              }}</a>
          </div>
        </el-footer>
      </el-container>
    </el-container>
  </el-container>
</template>

<script lang="js" setup>
import { ref } from 'vue'
const systems = [
  { index: '1', name: '一系统', url: '/system1/', description: '本系统的主要功能包括:音乐播放器,留言板,扫雷游戏,个人日志等' },
  { index: '2', name: '二系统', url: '/system2/', description: '本系统的主要功能包括:原神星铁文案查询,星铁账号查询,股票查询' },
  { index: '3', name: '三系统', url: '/system3/', description: '本系统的主要功能包括:托福,GRE等英文单词的记忆' },
]
const activeLang = ref('vue')
const ICP = ref('沪ICP备202405831号');
const open = url => {
  window.location.href = url;
};
</script>

<style>
.el-menu-demo .el-menu-item {
  color: #ffffff;
  background-color: #503131;
}

.title {
  font-family: 'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
  font-size: 20px;
}

.box-card {
  margin: 20px;
}

.el-header {
  background-color: #246e8e;
  color: #020202;
  text-align: center;
  line-height: 60px;
}

.el-footer {
  text-align: center;
  line-height: 60px;
  width: 100%;
  background-color: #000000;
}

.aside {
  height: 90vh;
  color: #000;
  background-color: #503131;
}

.box-card {
  margin: 20px;
  height: 100px;
  text-align: center;
  padding: 20px;
  transition: box-shadow 0.3s ease-in-out;
}

.box-card:hover {
  box-shadow: 0 0 10px rgba(0,0,0,0.5);
}
</style>