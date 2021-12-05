<template>
  <div>
 <div class="raka-customize__page">
      <div class="raka-customize-header">
        <input type="text" v-model="myWatchTitle" />
      </div>
      <div class="raka-customize-body" style="display: flex; flex-direction: row">
        <div class="raka-customize-body__aside">
          <nav>
            <ul class="raka-customize__manu-list">
              <li class="raka-customize__manu-item" 
                v-for="(feature, index) of featureList"
                :key="index"
                @click="selectedFeature = feature"
                :class="{ 'active': selectedFeature === feature}">
                {{ feature }}</li>
            </ul>
          </nav>
        </div>
        <div class="raka-customize-body__main">
          <template v-if="selectedFeature === 'SURFACE'">
            <CustomizeSetter
                ref="customizeSetter" />
          </template>
          <template v-else-if="selectedFeature === 'FUNCTION'">
            FUNCTION
          </template>
          <template v-else-if="selectedFeature === 'INK'">
            INK
          </template>
          <template v-else-if="selectedFeature === 'PACKAGE'">
            PACKAGE
          </template>
      </div>
    </div>
      <div class="raka-customize-footer">
        <button
          type="button"
          class="raka-customize-footer__temp-save-btn raka-btn"
          @click="saveSettings"
        >
          暫存設計
        </button>
        <button
          type="button"
          class="raka-customize-footer__confirm-btn raka-btn"
        >
          確認成品
        </button>
      </div>
  </div>
  </div>
</template>

<script>
import CustomizeSetter from "@/components/customize/CustomizeSetter.vue";
export default {
  name: "TheCustomizePage",
  components: {
      CustomizeSetter,
  },
  data() {
      return {
          myWatchTitle: '',
          selectedFeature: 'SURFACE',
          featureList: ['SURFACE', 'FUNCTION', 'INK', 'PACKAGE']
      }
  },
  methods: {
      saveSettings() {
        const myWatchSettings = {
          title: this.myWatchTitle,
          ...this.$refs.customizeSetter.myCustomWatch
        };
          console.log('myWatch', myWatchSettings);

      }
  }
};
</script>

<style scoped>
.raka-customize__manu-item.active {
    color: red;
}
</style>
