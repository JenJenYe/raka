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
            <SurfaceSetter
                ref="surfaceSetter" />
          </template>
          <template v-else-if="selectedFeature === 'FUNCTION'">
            <FunctionSetter />
          </template>
          <template v-else-if="selectedFeature === 'INK'">
            <InkSetter />
          </template>
          <template v-else-if="selectedFeature === 'PACKAGE'">
            <PackageSetter />
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
import SurfaceSetter from "@/components/customize/SurfaceSetter.vue";
import FunctionSetter from "@/components/customize/FunctionSetter.vue";
import InkSetter from "@/components/customize/InkSetter.vue";
import PackageSetter from "@/components/customize/PackageSetter.vue";

export default {
  name: "TheCustomizePage",
  components: {
      SurfaceSetter,
      FunctionSetter,
      InkSetter,
      PackageSetter,
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
          ...this.$refs.surfaceSetter.myCustomWatch
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
