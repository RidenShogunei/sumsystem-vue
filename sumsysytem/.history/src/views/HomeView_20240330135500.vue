<template>
  <el-container>
    <el-header class="title">
      <div>总系统</div>
    </el-header>
    <el-aside width="250px" class="aside">
      <el-menu
        :default-active="activeLang"
        class="el-menu-demo"
        mode="vertical"
        style="height: 100%; overflow-y: auto"
      >
        <el-menu-item index="vue">Vue</el-menu-item>
        <el-menu-item index="react">React</el-menu-item>
      </el-menu>
    </el-aside>
    <el-main>
      <el-row>
        <el-col :span="12" v-for="system in systems" :key="system.index">
          <el-card :body-style="{ padding: '0px' }" class="box-card">
            <div style="padding: 14px;">
              <a :href="system.url">{{ system.name }}</a>
            </div>
          </el-card>
        </el-col>
      </el-row>
    </el-main>
    <el-footer>
      <div class="footer">
        <a href="https://beian.miit.gov.cn" target="_blank" rel="noopener noreferrer">
          {{ ICP }}</a>
      </div>
      <p>All rights reserved.</p>
    </el-footer>
  </el-container>
</template>

<script lang="ts" setup>
import { ref } from 'vue'

const systems = [
  { index: '1', name: '一系统', url: '/system1/' },
  { index: '2', name: '二系统', url: '/system2/' },
  // 更多系统...
]

const activeLang = ref('vue')
const ICP = ref('沪ICP备202405831号');
</script>

<style>
.title{
  font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif;
}
.el-menu-vertical-demo {
  border-right: 1px solid #eee;
}
.box-card {
  margin: 20px;
}
.el-header, .el-footer {
  background-color: #b3c0d1;
  color: #020202;
  text-align: center;
  line-height: 60px;
}
.footer{
  width: 100%;
  text-align: center;
  background-color: #f8f9fa;
}
.aside {
  height: 100vh;
  background-color: gray;
}
</style>