<script setup lang="ts" generic="T extends any, O extends any">
defineOptions({
  name: 'IndexPage',
})

const name = ref('')

const router = useRouter()
function go() {
  if (name.value)
    router.push(`/hi/${encodeURIComponent(name.value)}`)
}
</script>

<template>
  <div class="bg">
    <div class="bg-cover">
      <!-- <img
        src="https://ug-drcn.dbankcdn.cn/nsp-campaign-res-drcn/campaignpreview/material/fa949bbdb13e4e6794b2525946db38d4/c3bf0c0c-1979-4a18-aa81-e2473472bc5f.PNG"
        alt=""> -->
    </div>
    <div class="orrignInput">
      <div i-carbon-campsite inline-block text-4xl />
      <div py-4 />
      <TheInput v-model="name" placeholder="What's your name?" autocomplete="false" @keydown.enter="go" />
      <div>
        <button class="m-3 text-sm btn" :disabled="!name" @click="go">
          Go
        </button>
      </div>
    </div>
    <div class="orrignInput">
      <div i-carbon-campsite inline-block text-4xl />
      <div py-4 />
      <TheInput v-model="name" placeholder="What's your name?" autocomplete="false" @keydown.enter="go" />
      <div>
        <button class="m-3 text-sm btn" :disabled="!name" @click="go">
          Go
        </button>
      </div>
    </div>
    <div class="orrignInput">
      <div i-carbon-campsite inline-block text-4xl />
      <div py-4 />
      <TheInput v-model="name" placeholder="What's your name?" autocomplete="false" @keydown.enter="go" />
      <div>
        <button class="m-3 text-sm btn" :disabled="!name" @click="go">
          Go
        </button>
      </div>
    </div>
    <div class="orrignInput">
      <div i-carbon-campsite inline-block text-4xl />
      <div py-4 />
      <TheInput v-model="name" placeholder="What's your name?" autocomplete="false" @keydown.enter="go" />
      <div>
        <button class="m-3 text-sm btn" :disabled="!name" @click="go">
          Go
        </button>
      </div>
    </div>
    <div class="orrignInput">
      <div i-carbon-campsite inline-block text-4xl />
      <div py-4 />
      <TheInput v-model="name" placeholder="What's your name?" autocomplete="false" @keydown.enter="go" />
      <div>
        <button class="m-3 text-sm btn" :disabled="!name" @click="go">
          Go
        </button>
      </div>
    </div>
    <div class="orrignInput">
      <div i-carbon-campsite inline-block text-4xl />
      <div py-4 />
      <TheInput v-model="name" placeholder="What's your name?" autocomplete="false" @keydown.enter="go" />
      <div>
        <button class="m-3 text-sm btn" :disabled="!name" @click="go">
          Go
        </button>
      </div>
    </div>
    <div class="orrignInput">
      <div i-carbon-campsite inline-block text-4xl />
      <div py-4 />
      <TheInput v-model="name" placeholder="What's your name?" autocomplete="false" @keydown.enter="go" />
      <div>
        <button class="m-3 text-sm btn" :disabled="!name" @click="go">
          Go
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.bg-cover {
  position: absolute;
  overflow: hidden;
  z-index: 0;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
}

.bg {
  width: 100%;
  height: 100%;
  position: relative;
  opacity: 1;
  background-image: url("https://ug-drcn.dbankcdn.cn/nsp-campaign-res-drcn/campaignpreview/material/fa949bbdb13e4e6794b2525946db38d4/c3bf0c0c-1979-4a18-aa81-e2473472bc5f.PNG");
  background-size: 100%;
  background-repeat: no-repeat;
  background-clip: content-box;
}

.orrignInput {
  /* position: absolute;
  bottom: 10%;
  left: 50%;
  transform: translate(-50%, -50%); */
  /* 透明度 */
  opacity: 0.2;
  background-color: antiquewhite;
}
</style>
