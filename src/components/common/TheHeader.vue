<template>
  <header class="text-gray-600 border-b">
    <div
      class="
        container
        flex flex-col flex-wrap
        items-center
        p-5
        mx-auto
        md:flex-row
      "
    >
      <a
        @click="handleClickLogo"
        class="
          flex
          items-center
          mb-4
          font-medium
          text-gray-900
          cursor-pointer
          md:mb-0
          hover:opacity-60
        "
      >
        <svg
          t="1616635695746"
          class="icon"
          viewBox="0 0 1024 1024"
          version="1.1"
          xmlns="http://www.w3.org/2000/svg"
          p-id="2049"
          width="40"
          height="40"
        >
          <path
            d="M859.648 159.744l-36.352-12.8c-4.096-23.552-25.6-42.496-51.2-42.496-29.696 0-53.248 23.552-53.248 53.248s23.552 53.248 53.248 53.248c14.848 0 25.6-6.144 36.352-14.848l29.696 12.8c23.552 8.704 38.4 38.4 38.4 66.048v473.6c0 27.648-14.848 57.344-38.4 66.048l-27.648 10.752c-10.752-10.752-23.552-16.896-38.4-16.896-29.696 0-53.248 23.552-53.248 53.248s23.552 53.248 53.248 53.248c23.552 0 42.496-14.848 51.2-36.352l38.4-12.8c45.056-14.848 78.848-66.048 78.848-115.2V275.456c-2.048-49.152-35.84-100.352-80.896-115.712zM292.352 808.448c-16.896 0-31.744 8.704-42.496 21.504l-38.4-12.8c-21.504-10.752-40.448-38.4-40.448-61.952V270.848c0-23.552 19.456-51.2 40.448-59.904l42.496-14.848c10.752 10.752 23.552 16.896 38.4 16.896 29.696 0 53.248-23.552 53.248-53.248s-23.552-53.248-53.248-53.248c-23.552 0-45.056 14.848-51.2 36.352l-53.248 16.896c-42.496 14.848-80.896 64-80.896 111.104v486.4c0 47.104 38.4 93.696 83.456 111.104l51.2 16.896c8.704 19.456 27.648 31.744 49.152 31.744 29.696 0 53.248-23.552 53.248-53.248 1.536-31.744-22.016-55.296-51.712-55.296z m125.952-388.096c0 23.552 18.944 42.496 42.496 42.496s42.496-18.944 42.496-42.496c0-23.552-18.944-42.496-42.496-42.496-23.552-0.512-42.496 18.944-42.496 42.496z"
            fill="#FF6A00"
            p-id="2050"
          ></path>
          <path
            d="M669.696 443.904l80.896 78.848 2.048 111.104-396.8-2.048v-66.048l91.648-66.048 89.6 59.904 132.608-115.712z"
            fill="#FF6A00"
            p-id="2051"
          ></path>
          <path
            d="M627.2 748.544H336.896c-49.152 0-89.6-40.448-89.6-89.6V424.448c0-23.552 19.456-42.496 42.496-42.496h8.704v275.456c0 21.504 16.896 36.352 36.352 36.352h332.8v10.752c2.048 25.088-16.896 44.032-40.448 44.032z"
            fill="#FF6A00"
            p-id="2052"
          ></path>
          <path
            d="M746.496 676.352h-394.24c-21.504 0-36.352-16.896-36.352-36.352V330.752c0-25.6 21.504-47.104 47.104-47.104h384c25.6 0 47.104 21.504 47.104 47.104v298.496c1.536 25.6-22.016 47.104-47.616 47.104z m-377.344-53.248H742.4V345.6c0-6.144-4.096-10.752-10.752-10.752H379.904c-6.144 0-10.752 4.096-10.752 10.752v277.504z"
            fill="#FF6A00"
            p-id="2053"
          ></path>
        </svg>
        <span class="ml-3 text-xl">Mt-Image-Classifier</span>
      </a>
      <nav
        class="flex flex-wrap items-center justify-center text-base md:ml-auto"
      >
        <router-link
          v-for="route in routeLists"
          :key="route.text"
          class="mr-5 cursor-pointer hover:text-gray-900"
          :active-class="'border-b-2 border-primary'"
          :to="{ name: route.name }"
        >
          {{ route.text }}
        </router-link>
      </nav>
    </div>
  </header>
</template>

<script>
import { useRouter } from 'vue-router'
export default {
  setup() {
    const router = useRouter()
    const handleClickLogo = () => {
      router.push({ name: 'ClassifierDefault' })
    }

    const routeLists = [
      { text: '圖片辨識(預設)', name: 'ClassifierDefault' },
      { text: '訓練模型', name: 'TrainModel' },
      { text: '圖片辨識(自訂)', name: 'ClassifierCustom' },
    ]

    return { handleClickLogo, routeLists }
  },
}
</script>
