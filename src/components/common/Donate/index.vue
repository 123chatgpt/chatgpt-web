<script setup lang="ts">
import { computed } from 'vue'
import { NImage, NImageGroup, NModal, NSpace } from 'naive-ui'
import wechatPayImg from '@/assets/WechatPay.jpeg'
import aliPayImg from '@/assets/AliPay.jpeg'
interface Props {
  visible: boolean
}

interface Emit {
  (e: 'update:visible', visible: boolean): void
}

const props = defineProps<Props>()

const emit = defineEmits<Emit>()

const show = computed({
  get: () => props.visible,
  set: (visible: boolean) => emit('update:visible', visible),
})
</script>

<template>
  <NModal v-model:show="show" style="width: 90%; max-width: 600px;" preset="card">
    <div class="flex flex-col items-center space-y-4">
      <div class="flex flex-col items-center mb-4">
        <span>服务器昂贵，接口昂贵，但网站免费</span>
        <span>如果您觉得做的好，可以给我买一瓶冰阔落～</span>
      </div>
      <NImageGroup show-toolbar-tooltip>
        <NSpace>
          <NImage
            width="200"
            :src="wechatPayImg"
          />
          <NImage
            width="200"
            :src="aliPayImg"
          />
        </NSpace>
      </NImageGroup>
    </div>
  </NModal>
</template>

<style scoped>

</style>
