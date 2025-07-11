<template>
  <!-- 页面内容容器（必需） -->
  <view class="container">
    <!-- 安全顶部容器（H5不必） -->
    <wd-toast />
    <!-- 页面内容 -->
    <view class="content">
      <!--在这里编写页面主体内容-->
    </view>
  </view>
</template>

<script setup>
import { ref } from "vue"
import SafeCapsaulContainer from "@/components/SafeCapsaulContainer"
import SuitCapsaulNavibar from "@/components/SuitCapsaulNavibar"
import {
  useNavigate,
  useSwitchTab,
  flattenToNestedObject,
} from "@/hooks/useNavigate" // 页面导航、tabbar导航、路由参数转化对象方法（必需）

// wd的吐司弹窗提示组件
import { useToast } from "@/uni_modules/wot-design-uni"
const toast = useToast()

// ======================== 页面数据加载（可选） ======================
onLoad(async (options) => {
  console.log("------------------------- {xxx} --------------------------")
  const NestedObjectOptions = flattenToNestedObject(options)
  console.log("NestedObjectOptions", NestedObjectOptions)
})

// ================== 路由跳转相关 ==================

// 简单的返回上一级页面，使用uni.navigateBack
const handleClickLeft = () => {
  uni.navigateBack()
}

// 复杂的路由跳转,普通子页面使用封装好的： useNavigate
const jumpXxxPage = () => {
  useNavigate("/pages/Xxx/index", { ...params })
}

// 复杂的路由跳转,tabbar页面使用封装好的： useSwitchTab
const jumpXxxTabbar = () => {
  useSwitchTab("/pages/Xxx/index", { ...params })
}
</script>

<style lang="scss" scoped>
// 页面容器（必需）
.container {
  width: 100%;
  min-height: 100vh;
  box-sizing: border-box; // 若页面涉及padding，统一在padding后续上：box-sizing: border-box;

  // 建议的flex布局（可选）
  display: flex;
  flex-direction: column;
  align-items: center;
}
// 页面内容
.content {
  width: 100%;
  min-height: 100vh;
  // padding: 12px; // (可选，建议用padding去挤占子内容)
  box-sizing: border-box;
}
</style>
