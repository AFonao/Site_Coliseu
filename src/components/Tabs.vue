<template>

    <div v-if="$isMobile()">
      <div>
        <md-button class="md-icon-button"
          v-for="(item, index) in tabName"
          @click="switchPanel(tabName[index])"
          :key="item"
          :class="[
              { active: isActivePanel(tabName[index]) },
              { [getColorButton(colorButton)]: isActivePanel(tabName[index]) }
            ]"
        >
          <md-icon><img :src="tabIcon[index]" alt="People" class="img-icon-button"></md-icon>
          <span class="text-button">{{ tabName[index] }}</span>
        </md-button>

        <transition name="fade" mode="out-in">
          <div class="tab-content">
            <div
              :class="getTabContent(index + 1)"
              v-for="(item, index) in tabName"
              :key="item"
              v-if="isActivePanel(tabName[index])"
            >
              <slot :name="getTabContent(index + 1)">
                This is the default text!
              </slot>
            </div>
          </div>
        </transition>
      </div>
    </div>
    <div v-else>
      <md-card
        class="md-card-tabs"
        :class="[
          { 'flex-column': flexColumn },
          { 'nav-pills-icons': navPillsIcons },
          { 'md-card-plain': plain }
        ]"
      >
          <md-card-header slot="header-title"> </md-card-header>
          <md-card-content>
            <md-list class="md-triple-line">
              <md-list-item
                v-for="(item, index) in tabName"
                @click="switchPanel(tabName[index])"
                :key="item"
                :class="[
                  { active: isActivePanel(tabName[index]) },
                  { [getColorButton(colorButton)]: isActivePanel(tabName[index]) }
                ]"
              >
                {{ tabName[index] }}
                <!-- <md-icon v-if="navPillsIcons">{{ tabIcon[index] }}</md-icon> -->
                <img v-if="navPillsIcons" :src="tabIcon[index]" class="img-icon" />
              </md-list-item>
            </md-list>

            <transition name="fade" mode="out-in">
              <div class="tab-content">
                <div
                  :class="getTabContent(index + 1)"
                  v-for="(item, index) in tabName"
                  :key="item"
                  v-if="isActivePanel(tabName[index])"
                >
                  <slot :name="getTabContent(index + 1)">
                    This is the default text!
                  </slot>
                </div>
              </div>
            </transition>
          </md-card-content>
      </md-card>
    </div>
   
</template>

<script>
export default {
  props: {
    flexColumn: Boolean,
    navPillsIcons: Boolean,
    plain: Boolean,
    tabName: Array,
    tabIcon: Array,
    colorButton: {
      type: String,
      default: ""
    }
  },
  data() {
    return {
      activePanel: this.tabName[0],
    };
  },
  methods: {
    switchPanel(panel) {
      this.activePanel = panel;
    },
    isActivePanel(panel) {
      return this.activePanel == panel;
    },
    getColorButton: function(colorButton) {
      console.log("md-" + colorButton + "");
      console.log(this.$isMobile());
      return "md-" + colorButton + "";
    },
    getTabContent: function(index) {
      return "tab-pane-" + index + "";
    }
  }
  
};
</script>

<style lang="css" scoped>
.img-icon {
  max-width: 50%;
  filter: invert(1);
}
.md-list-item-button{
    background-color: #6a0201 !important;
}

.md-icon-button{
  width: 32% !important;
  height: 60px !important;
  background-color: #6a0201 !important;
  
}

.img-icon-button{
  max-width: 90%;
  filter: invert(1);
  margin: 10px;
}

.text-button{
  font-weight: bold;
  letter-spacing: 1px;
  text-align: center;
  padding-left: 1.25em;
  font-size: 5px !important;
  line-height: 2.5 !important;
}

</style>
