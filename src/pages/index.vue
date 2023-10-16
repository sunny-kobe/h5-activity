<script setup lang="ts" generic="T extends any, O extends any">
defineOptions({
  name: 'IndexPage',
})

const isMuted = ref(false)
const isMaskVisible = ref(false)
const ruleDialogVisible = ref(false)
const shareDialogVisible = ref(false)
const isAppointment = ref(false) // 预约游戏
// 拖动
const mariner = ref(null)
const isDragging = ref(false)
const startX = ref(0)
const scrollX = ref(0)
const characters = ref([
  { id: 1, name: '白凤', image: '~/assets/images/character/character1.jpg' },
  { id: 2, name: '赤练', image: 'character2.jpg' },
  { id: 3, name: '盗跖', image: 'character3.jpg' },
  // 添加更多角色
])

function toggleMute() {
  isMuted.value = !isMuted.value
  // 在这里添加切换音频状态的逻辑
  // 暂停或恢复音频播放
}
function showMask() {
  isMaskVisible.value = true
}
function hideMask() {
  isMaskVisible.value = false
}

// 规则
function showRoules() {
  showMask()
  ruleDialogVisible.value = true
}
function hideRuleDialog() {
  ruleDialogVisible.value = false
  hideMask()
}

// 分享
function showShare() {
  showMask()
  shareDialogVisible.value = true
}
function hideShareDialog() {
  shareDialogVisible.value = false
  hideMask()
}

function startDragging(event: { clientX: number }) {
  // console.log("startDragging");
  isDragging.value = true
  startX.value = event.clientX - scrollX.value
}

function dragCharacter(event: { clientX: number }) {
  // console.log("dragCharacter");
  if (!isDragging.value)
    return
  const deltaX = event.clientX - startX.value
  scrollX.value = deltaX
}

function stopDragging() {
  // console.log("stopDragging");
  isDragging.value = false
}
</script>

<template>
  <div class="bg">
    <!-- 遮罩层 -->
    <div v-if="isMaskVisible" class="mask" />
    <!-- 右上角挂件 -->
    <div class="pendant">
      <!-- 分享 -->
      <svg
        t="1697424890611" class="share" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"
        p-id="4120" width="200" height="200" @click="showShare"
      >
        <path
          d="M911.6 651.6l0 209.2c0 36-30.4 66.2-66.2 66.2l-699.6 1.2c-35.8 0-65-29.2-65-65.2l1.2-699.6c0-35.8 30.4-66.2 66.2-66.2l387 0L535.2 20.2 148.2 20.2c-81.8 0-143 82.8-143 156.8l0 686c0 77.6 63 140.8 140.8 140.8l686 0c82 0 156.6-68.2 156.6-143L988.6 651.6 911.6 651.6 911.6 651.6zM730.2 60.8l288.6 289.2L730.2 639l0-165.2c0 0-286.4-31.8-453.6 206.6 0 0 52.6-454.4 453.6-454.4L730.2 60.8 730.2 60.8z"
          fill="#272636" p-id="4121"
        />
      </svg>
      <!-- 规则 -->
      <svg
        t="1697425114194" class="rules" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"
        p-id="5242" width="200" height="200" @click="showRoules"
      >
        <path
          d="M634.7 164H380.3c-14.6 0-26.3-11.8-26.3-26.3V27.3C354 12.8 365.8 1 380.3 1h254.3C649.2 1 661 12.8 661 27.3v110.3c0 14.6-11.8 26.4-26.3 26.4z"
          fill="#2c2c2c" p-id="5243"
        />
        <path
          d="M870.3 99H723.6c-4.9 0-8.8 4-8.8 8.8v75.3c0 14.6-11.8 26.3-26.3 26.3H335.1c-14.6 0-26.3-11.8-26.3-26.3v-75.3c0-4.9-4-8.8-8.8-8.8H153.2c-35.9 0-65 29.1-65 65v794c0 35.9 29.1 65 65 65h717.1c35.9 0 65-29.1 65-65V164c0-35.9-29.1-65-65-65zM167 362c0-17.7 14.3-32 32-32h514c17.7 0 32 14.3 32 32s-14.3 32-32 32H199c-17.7 0-32-14.3-32-32z m251 473c0 17.7-14.3 32-32 32H199c-17.7 0-32-14.3-32-32s14.3-32 32-32h187c17.7 0 32 14.3 32 32z m0-157.7c0 17.7-14.3 32-32 32H199c-17.7 0-32-14.3-32-32s14.3-32 32-32h187c17.7 0 32 14.4 32 32z m62-125.6H199c-17.7 0-32-14.3-32-32s14.3-32 32-32h281c17.7 0 32 14.3 32 32 0 17.6-14.3 32-32 32z m203 382.4c-99.4 0-180-41.4-180-92.5 0-12.8 5.1-25 14.2-36.1 27.4 33.1 91.3 56.4 165.8 56.4s138.4-23.2 165.8-56.4c9.2 11.1 14.2 23.3 14.2 36.1 0 51.1-80.6 92.5-180 92.5z m0-102.6c-99.4 0-180-41.4-180-92.5 0-13.3 5.5-25.9 15.3-37.4 27.9 32.5 91.2 55.1 164.7 55.1s136.7-22.7 164.7-55.1C857.5 713 863 725.7 863 739c0 51.1-80.6 92.5-180 92.5z m0-102.6c-99.4 0-180-41.4-180-92.5s80.6-92.5 180-92.5 180 41.4 180 92.5-80.6 92.5-180 92.5z"
          fill="#2c2c2c" p-id="5244"
        />
      </svg>
      <!-- 声音 -->
      <svg
        t="1697425251769" :class="isMuted ? 'mute' : 'voice'" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"
        p-id="6716" width="200" height="200" @click="toggleMute"
      >
        <path
          v-if="!isMuted"
          d="M257.493333 322.4l215.573334-133.056c24.981333-15.413333 57.877333-7.914667 73.493333 16.746667 5.301333 8.373333 8.106667 18.048 8.106667 27.914666v555.989334C554.666667 819.093333 530.784 842.666667 501.333333 842.666667c-9.994667 0-19.786667-2.773333-28.266666-8L257.493333 701.6H160c-41.237333 0-74.666667-33.013333-74.666667-73.738667V396.138667c0-40.725333 33.429333-73.738667 74.666667-73.738667h97.493333z m26.133334 58.4a32.298667 32.298667 0 0 1-16.96 4.8H160c-5.888 0-10.666667 4.714667-10.666667 10.538667v231.733333c0 5.813333 4.778667 10.538667 10.666667 10.538667h106.666667c5.994667 0 11.872 1.664 16.96 4.8L490.666667 770.986667V253.013333L283.626667 380.8zM800.906667 829.653333a32.288 32.288 0 0 1-45.248-0.757333 31.317333 31.317333 0 0 1 0.768-44.693333c157.653333-150.464 157.653333-393.962667 0-544.426667a31.317333 31.317333 0 0 1-0.768-44.682667 32.288 32.288 0 0 1 45.248-0.757333c183.68 175.306667 183.68 460.010667 0 635.317333z m-106.901334-126.186666a32.288 32.288 0 0 1-45.248-1.216 31.328 31.328 0 0 1 1.237334-44.672c86.229333-80.608 86.229333-210.56 0-291.178667a31.328 31.328 0 0 1-1.237334-44.672 32.288 32.288 0 0 1 45.248-1.216c112.885333 105.546667 112.885333 277.418667 0 382.965333z"
          fill="#000000" p-id="6717"
        />
        <path
          v-if="isMuted"
          d="M128 420.576v200.864h149.12l175.456 140.064V284.288l-169.792 136.288H128z m132.256-64l204.288-163.968a32 32 0 0 1 52.032 24.96v610.432a32 32 0 0 1-51.968 24.992l-209.92-167.552H96a32 32 0 0 1-32-32v-264.864a32 32 0 0 1 32-32h164.256zM752 458.656L870.4 300.8a32 32 0 1 1 51.2 38.4L792 512l129.6 172.8a32 32 0 0 1-51.2 38.4l-118.4-157.856-118.4 157.856a32 32 0 0 1-51.2-38.4l129.6-172.8-129.6-172.8a32 32 0 0 1 51.2-38.4l118.4 157.856z"
          fill="#000000" p-id="6871"
        />
      </svg>
    </div>
    <div class="kv">
      <span class="kvMain">KV</span>
      <div class="logo">
        logo
      </div>
      <div class="theme">
        <span class="themePre">预抽</span>
        <span class="themeText">
          必得命定五星
          <br>
          约你共赴香波地岛
        </span>
      </div>
      <div class="activityTime">
        活动时间: XXXX-XXXX
      </div>
    </div>
    <!-- 预约游戏 -->
    <div class="appointment">
      <div v-if="!isAppointment" class="noAppointment">
        预约游戏
      </div>
      <div v-if="isAppointment" class="succussAppointment">
        已成功预约游戏
      </div>
      <div class="appointmentText">
        (成功预约，免费十连抽)
      </div>
    </div>

    <!-- 招募 -->
    <div class="recruit">
      <div class="recruitYours">
        招募你的船员
      </div>
      <p>角色一览</p>
      <!-- 横向滚动查看角色 -->
      <div ref="mariner" class="mariner" @mousedown="startDragging" @mousemove="dragCharacter" @mouseup="stopDragging">
        <div class="scrollable-area" :style="{ transform: `translateX(${scrollX}px)` }">
          <div v-for="character in characters" :key="character.id" class="character">
            <img :src="character.image" :alt="character.name">
            <p>{{ character.name }}</p>
          </div>
        </div>
      </div>
    </div>

    <!-- 规则弹窗 -->
    <div v-if="ruleDialogVisible" class="ruleDialog">
      <h2>规则</h2>
      <p>在这里放置规则内容...</p>
      <button @click="hideRuleDialog">
        关闭
      </button>
    </div>
    <!-- 分享弹窗 -->
    <div v-if="shareDialogVisible" class="ruleDialog">
      <h2>分享</h2>
      <p>在这里放置分享内容...</p>
      <button @click="hideShareDialog">
        关闭
      </button>
    </div>
  </div>
</template>

<style  scoped>
.mask {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  /* 半透明黑色背景 */
  z-index: 999;
  /* 遮罩层在最上层 */
  display: flex;
  justify-content: center;
  align-items: center;
}

.bg {
  width: 100%;
  height: 1800px;
  position: relative;
  opacity: 1;
  background-image: url("~@/assets/bg.png");
  background-size: 100%;
  background-repeat: no-repeat;
  background-clip: content-box;
  color: #000;
  font-size: 16px;
}

.kv {
  width: 100%;
  height: 220px;
  background: #757171;
}

.kvMain {
  /* 居中 */
  position: absolute;
  top: 120px;
  left: 50%;
  transform: translate(-50%, -50%);
}

.logo {
  width: 80px;
  height: 30px;
  /* 字体居中 */
  text-align: center;
  position: absolute;
  top: 100px;
  left: 0;
  background-color: #383636;
}

.theme {
  width: 300px;
  height: 80px;
  /* 字体居中 */
  text-align: center;
  position: absolute;
  top: 150px;
  left: 40px;
  transform: rotate(-15deg);
  display: inline-block;
  background-color: #3a3434;
  /* 背景色用于突出显示倾斜效果 */
  padding: 10px;
  /* 适当的内边距 */
}

.themePre {
  width: 20px;
  height: 50px;
  position: absolute;
  top: 10px;
  left: 40px;
  transform: rotate(15deg);
  background-color: #a79e9e;
}

.themeText {
  width: 100px;
  height: 60px;
}

.activityTime {
  width: 300px;
  height: 20px;
  text-align: center;
  position: absolute;
  top: 270px;
  left: 40px;
  display: inline-block;
  background-color: #a79f9f;
}

.share {
  width: 20px;
  height: 20px;
  position: absolute;
  top: 20px;
  right: 20px;
}

.rules {
  width: 20px;
  height: 25px;
  position: absolute;
  top: 60px;
  right: 20px;
}

.voice,
.mute {
  width: 20px;
  height: 20px;
  position: absolute;
  top: 100px;
  right: 20px;
}

/* 预约游戏 */
.appointment {
  width: 140px;
  height: 40px;
  position: absolute;
  top: 320px;
  left: 50%;
  transform: translate(-50%, -50%);
  background: rgb(207, 204, 198);
  padding: 5px;
  text-align: center;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
}

.appointmentText {
  font-size: 12px;
  color: #000;
  margin-top: 10px;
}

/* 招募 */
.recruit {
  width: 340px;
  height: 200px;
  position: absolute;
  top: 500px;
  left: 50%;
  transform: translate(-50%, -50%);
  background: rgb(134, 132, 130);
}

.recruitYours {
  font-size: 30px;
  color: #000;
  margin-top: -22px;
}

.mariner {
  overflow-x: scroll;
  width: 300px;
  border: 1px solid #ccc;
  margin: 20px 0;
  cursor: grab;
}

.scrollable-area {
  display: flex;
  transition: transform 0.3s ease;
}

.character {
  flex: 0 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 10px;
  width: 150px;
}

.character img {
  width: 100px;
  height: 100px;
  object-fit: cover;
  border: 1px solid #ddd;
  /* border-radius: 50%; */
}

/* 弹窗 */
.ruleDialog {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: #fff;
  padding: 20px;
  z-index: 999;
  /* 对话框在遮罩层之上 */
  text-align: center;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);

}

.ruleDialog h2 {
  font-size: 24px;
  margin-bottom: 10px;
}

.ruleDialog button {
  background: #007bff;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin-top: 10px;
  cursor: pointer;
  te;
