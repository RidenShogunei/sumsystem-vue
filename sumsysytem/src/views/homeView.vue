<template>
  <el-container direction="vertical">
    <el-header class="title">
      <div :style="{ color: 'white' }">总系统</div>
    </el-header>
    <el-container>
      <div class="aside">
        <el-aside width="250px" class="aside">
          <el-menu
            :default-active="activeLang"
            class="el-menu-demo"
            mode="vertical"
            style="height: 100%; overflow-y: auto"
          >
            <el-menu-item index="vue" @click="activeLang = 'vue'"
              >Vue</el-menu-item
            >
            <!-- 这里添加 @click -->
            <el-menu-item index="react" @click="activeLang = 'react'"
              >React</el-menu-item
            >
            <!-- 这里添加 @click -->
          </el-menu>
        </el-aside>
      </div>
      <el-container>
        <el-main>
          <el-row :gutter="20">
            <el-col
              v-for="system in systems"
              :key="system.index"
            >
              <el-card
                :body-style="{ padding: '0px' }"
                class="box-card"
                @click="open(system.url)"
              >
                <div style="padding: 14px">
                  {{ system.name }}
                </div>
                <div>
                  {{ system.description }}
                </div>
                <div v-if="system.name === '五系统'">
                <br>
                <el-button type='primary' @click.stop="downloadFile" :style="{ 'margin-bottom': '2%' }">点击下载配套使用app</el-button>
        
                </div>
              </el-card>
            </el-col>
          </el-row>
        </el-main>
        <el-footer>
          <div class="footer">
            <a
              href="https://beian.miit.gov.cn"
              target="_blank"
              rel="noopener noreferrer"
              style="color: white"
              >{{ ICP }}</a
            >
          </div>
        </el-footer>
      </el-container>
    </el-container>
  </el-container>
</template>

<script lang="js" setup>
import { ref, computed } from 'vue'
const downloadFile = async () => {
        let filePath = 'FifthSys.apk';
        const apiUrl = "https://chenjinxu.top:6002";
        const mid = 'document/uploads';
        const fullPath = `${apiUrl}/${mid}/${filePath}`;

        try {
            const response = await fetch(fullPath);
            if (!response.ok) {
                throw new Error('Network response was not ok');
            }
            const blob = await response.blob();
            const url = window.URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = filePath || 'download';
            document.body.appendChild(a); // we need to append the element to the dom -> otherwise it will not work in firefox
            a.click();
            a.remove();  //afterwards we remove the element again
        } catch (error) {
            alert('文件下载失败');
        }
    };

const vueSystems = [
  { index: '1', name: '一系统', url: '/system1/', description: '本系统的主要功能包括:音乐播放器,留言板,扫雷游戏,个人日志等' },
  { index: '2', name: '二系统', url: '/system2/', description: '本系统的主要功能包括:原神星铁文案查询,星铁账号查询,股票查询' },
  { index: '3', name: '三系统', url: '/system3/', description: '本系统的主要功能包括:托福,GRE等英文单词的记忆' },
  { index: '4', name: '四系统', url: '/system4/', description: '本系统的主要功能包括:通信功能，原理包括轮询和websocket' },
]

const reactSystems = [
  { index: '1', name: '五系统', url: '/system5/', description: '本系统的主要功能包括:文件，音频，视频的上传，录制，下载和管理' },
  //... 更多 React 系统
]

const activeLang = ref('vue')
const ICP = ref('沪ICP备202405831号');
const open = url => {
  window.location.href = url;
};

const systems = computed(() => {
  return activeLang.value === 'vue' ? vueSystems : reactSystems;
})
</script>

<style>
.el-menu-demo .el-menu-item {
  color: #ffffff;
  background-color: #503131;
}

.title {
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
  font-size: 20px;
}

.box-card {
  margin: 20px;
  height: auto;
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
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
}
</style>
