<template>
  <div class="flex items-center justify-center bg-grey-lighter">
    <label
      class="
        w-64
        flex flex-col
        items-center
        px-4
        py-6
        bg-white
        text-primary
        rounded-lg
        shadow-lg
        tracking-wide
        border border-primary
        cursor-pointer
        hover:bg-primary
        hover:text-white
      "
    >
      <svg
        class="w-8 h-8"
        fill="currentColor"
        xmlns="http://www.w3.org/2000/svg"
        viewBox="0 0 20 20"
      >
        <path
          d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z"
        />
      </svg>
      <span class="mt-2 text-base leading-normal font-medium">上傳圖片</span>
      <span class="text-sm">Max 2MB each.</span>
      <input
        type="file"
        class="hidden"
        accept="image/*"
        @change="beforeUpload"
        @click="reset"
        :multiple="multipleFile"
      />
    </label>
  </div>
</template>
<script>
export default {
  props: {
    multipleFile: {
      type: Boolean,
      default: false,
    },
    fileLimitSize: {
      type: Number,
      default: 2 * 1024 * 1024,
    },
  },
  emits: ['upload'],
  setup(props, ctx) {
    const beforeUpload = (e) => {
      const fileLists = [...e.target.files].filter(
        (file) => file.size < props.fileLimitSize
      )
      ctx.emit('upload', fileLists)
    }

    const reset = (e) => {
      e.target.value = ''
    }
    return { beforeUpload, reset }
  },
}
</script>
<style></style>
