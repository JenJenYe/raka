<template>
  <div class="raka-customize">
    <ul class="raka-customize__list">
      <li 
        v-for="(element, index) of watchElements"
        :key="index"
        class="raka-customize__item" 
        @click="clickTab(element)">{{ element }}</li>
    </ul>
    <div class="raka-customize__selector">
      <div v-show="selectedWatchElement === 'FRAME'" style="display: flex">
        <a
          v-for="(frame, index) of frameList"
          :key="index"
          @click="setWatchElement('frame', frame.title)"
        >
          <img :src="frame.imgUrl" style="width: 100px" />
          <div>{{ frame.title }}</div>
        </a>
      </div>
      <div v-show="selectedWatchElement === 'OUTWARD'">
        <button type="button" @click="setWatchElement('outward', '11111')">
          1111
        </button>
      </div>
      <div v-show="selectedWatchElement === 'STRAPE'">STRAPE</div>
      <div v-show="selectedWatchElement === 'HANDS'">HANDS</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CustomizeSetter",
  data() {
    return {
        selectedWatchElement: 'FRAME',
        watchElements: ['FRAME', 'OUTWARD', 'STRAPE', 'HANDS'],
        myCustomWatch: {
          frame: '',
          outward: '',
          strape: '',
          hands: '',
        },
      frameList: [
        {
          title: '玫瑰金',
          imgUrl:
            'https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/MKY23ref_VW_34FR+watch-44-alum-gold-nc-se_VW_34FR_WF_CO_GEO_TW?wid=750&hei=712&trim=1%2C0&fmt=p-jpg&qlt=95&.v=1630364847000%2C1630708211000',
        },
        {
          title: '太空灰',
          imgUrl:
            'https://store.storeimages.cdn-apple.com/8756/as-images.apple.com/is/MKUQ3_VW_34FR+watch-45-alum-midnight-nc-7s_VW_34FR_WF_CO?wid=1400&hei=1400&trim=1,0&fmt=p-jpg&qlt=95&.v=1632171067000,1631661671000',
        },
      ],
    }
  },
  methods: {
    setWatchElement(elementName, elementValue) {
      this.myCustomWatch[elementName] = elementValue;
    },
    clickTab(elementName) {
      this.selectedWatchElement = elementName;
    }
  }
};
</script>

<style scoped>

</style>
