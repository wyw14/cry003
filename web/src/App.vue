<script setup lang="ts">const modules = ["白名单扫描源", "任务执行", "SSE 进度重放", "取消恢复和结果审计"]</script>
<template><main><h1>实时文件扫描与进度中心</h1><ul><li v-for="item in modules" :key="item">{{ item }}</li></ul></main></template>
<style>body{font-family:system-ui;background:#f5f7fb}main{max-width:900px;margin:3rem auto;background:white;padding:2rem;border-radius:16px}</style>
