<script setup lang="ts">
import { computed } from 'vue'

interface Props {
  bgColor?: string
}

const props = withDefaults(defineProps<Props>(), {
  bgColor: '#F7282A',
})

// 验证颜色格式是否合法（支持 #RGB, #RRGGBB, #RRGGBBAA 格式）
const isValidColor = (color: string): boolean => {
  const hexColorRegex = /^#([A-Fa-f0-9]{3}|[A-Fa-f0-9]{6}|[A-Fa-f0-9]{8})$/
  return hexColorRegex.test(color)
}

// 计算最终使用的背景颜色
const backgroundColor = computed(() => {
  return isValidColor(props.bgColor) ? props.bgColor : '#F7282A'
})
</script>

<template>
  <div class="home-view" :style="{ backgroundColor: backgroundColor }"></div>
</template>

<style scoped>
.home-view {
  width: 100%;
  height: 100vh;
  background-image: url('@/assets/svg/vector.svg');
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}
</style>
