<template>
  <!-- <main font-sans p="x-4 y-10" text="center gray-700 dark:gray-200"> -->
  <main font-sans text=" gray-700 dark:gray-200" class="app-background">
    <RouterView />
    <!-- <TheFooter /> -->
  </main>
</template>

<style>
.app-background {
  background-image: url('https://ug-drcn.dbankcdn.cn/nsp-campaign-res-drcn/campaignpreview/material/fa949bbdb13e4e6794b2525946db38d4/c3bf0c0c-1979-4a18-aa81-e2473472bc5f.PNG');
  background-size: cover;
  background-repeat: no-repeat;
  /* 其他样式属性，如背景颜色等 */
  min-height: 100vh;
}
</style>
