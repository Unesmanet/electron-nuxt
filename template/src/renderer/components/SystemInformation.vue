<template>
  <div>
    <div class="title">Information</div>
    <div class="items">
      <div class="item">
        <div class="name">Nuxt.js:</div>
        <div class="value">
          {{ nuxt }}
          {{ system.nuxt }}
        </div>
      </div>
      <div class="item">
        <div class="name">Vue.js:</div>
        <div class="value">
          {{ vue }}
          {{ system.vue }}
        </div>
      </div>
      <div class="item">
        <div class="name">Electron:</div>
        <div class="value">
          {{ electron }}
          {{ system.electron }}
        </div>
      </div>
      <div class="item">
        <div class="name">Node:</div>
        <div class="value">
          {{ node }}
          {{ system.node }}
        </div>
      </div>
      <div class="item">
        <div class="name">Chrome:</div>
        <div class="value">
          {{ chrome }}
          {{ system.chrome }}
        </div>
      </div>
      <div class="item">
        <div class="name">Platform:</div>
        <div class="value">
          {{ platform }}
          {{ system.platform }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      system: {
        chrome: '',
        electron: '',
        node: '',
        platform: '',
        vue: '',
        nuxt: ''
      }
    };
  },

  mounted () {
    this.listenSystemDataReception()
    Object.keys(this.system).forEach(element => {
      this.getSystemInformation(element)
    })
  },

  methods: {
    getSystemInformation (element) {
      window.ipcRenderer.send('get-system-information', element)
    },
    listenSystemDataReception () {
      window.ipcRenderer.receive('get-system-information', (element, data) => {
        this.system[element] = data
      })
    }
  }
};
</script>

<style scoped>
.title {
  color: #364758;
  font-size: 1.5em;
  letter-spacing: 0.25px;
  margin-top: 10px;
}
.items {
  margin-top: 8px;
}
.item {
  display: flex;
  margin-bottom: 6px;
}
.item .name {
  color: #6a6a6a;
  margin-right: 6px;
}

.item .value {
  color: #364758;
  font-weight: bold;
}
</style>
