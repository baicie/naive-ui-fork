<markdown>
# Change file on finish

You can change a file's properties after its upload has finished.
</markdown>

<script lang="ts">
import type { UploadFileInfo } from 'naive-ui'
import { useMessage } from 'naive-ui'
import { defineComponent } from 'vue'

export default defineComponent({
  setup() {
    const message = useMessage()
    const handleFinish = ({
      file,
      event
    }: {
      file: UploadFileInfo
      event?: ProgressEvent
    }) => {
      message.success((event?.target as XMLHttpRequest).response)
      const ext = file.name.split('.')[1]
      file.name = `renamed.${ext}`
      file.url = '__HTTP__://www.mocky.io/v2/5e4bafc63100007100d8b70f'
      return file
    }
    return {
      message,
      handleFinish
    }
  }
})
</script>

<template>
  <n-upload
    action="__HTTP__://www.mocky.io/v2/5e4bafc63100007100d8b70f"
    @finish="handleFinish"
  >
    <n-button>Upload</n-button>
  </n-upload>
</template>
