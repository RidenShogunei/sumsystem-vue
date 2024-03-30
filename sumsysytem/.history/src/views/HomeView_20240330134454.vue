<template>
    <el-container>
      <el-aside width="200px">
        <el-menu
          :default-active="activeLang"
          class="el-menu-demo"
          mode="vertical"
          @select="handleLangSelect"
        >
          <el-menu-item index="vue">Vue</el-menu-item>
          <el-menu-item index="react">React</el-menu-item>
        </el-menu>
      </el-aside>
      <el-main>
        <el-row>
          <el-col :span="8" v-for="system in systems" :key="system.index">
            <el-card :body-style="{ padding: '0px' }" class="box-card">
              <div style="padding: 14px;">
                <a :href="system.url">{{ system.name }}</a>
              </div>
            </el-card>
          </el-col>
        </el-row>
      </el-main>
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
  
  const handleLangSelect = (key) => {
    activeLang.value = key
  }
  </script>
  
  <style>
  .el-menu-vertical-demo {
    border-right: 1px solid #eee;
  }
  .box-card {
    margin: 20px;
  }
  </style>