<template>
  <div>
    <BaseUploadBtn @upload="uploadImg" :multiple-file="false" class="mt-10" />
    <ClassifierResult :img="img" :result-lists="resultLists" />
  </div>
</template>

<script>
import useMl5 from '/@/componsable/useMl5'
import BaseUploadBtn from '/@/components/common/BaseUploadBtn.vue'
import ClassifierResult from '/@/components/Classifier/ClassifierResult.vue'
import { computed, ref, watch, watchEffect } from 'vue'
import { useRoute } from 'vue-router'

export default {
  components: { BaseUploadBtn, ClassifierResult },
  setup() {
    const img = ref('')
    const resultLists = ref([
      {
        label: '請上傳圖片',
        confidence: 1,
      },
    ])
    const { getDefaultClassifier, getCustomClassifier } = useMl5()

    const route = useRoute()
    const routeName = computed(() => route.name)
    let classifier
    watchEffect(async () => {
      if (routeName === 'TrainModel') return
      if (routeName.value === 'ClassifierCustom') {
        classifier = await getCustomClassifier()
        return
      }
      classifier = await getDefaultClassifier()
    })

    const predict = (img) => {
      const imageObj = new Image()
      imageObj.onload = () => {
        classifier.classify(imageObj, (err, results) => {
          resultLists.value = results.sort(
            (a, b) => b.confidence - a.confidence
          )
        })
      }
      imageObj.src = img
    }

    const uploadImg = (fileLists) => {
      const file = fileLists[0]
      img.value = URL.createObjectURL(file)
      predict(img.value)
    }

    return { img, resultLists, uploadImg }
  },
}
</script>

<style></style>
