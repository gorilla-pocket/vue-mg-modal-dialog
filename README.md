# vue-mg-modal-dialog

![npm](https://img.shields.io/npm/v/vue-mg-modal-dialog)
![npm](https://img.shields.io/npm/dm/vue-mg-modal-dialog)

## Installation

```
npm i vue-mg-modal-dialog
```

## Usage

app.js

```javascript
import ModalDialog from 'vue-mg-modal-dialog'
Vue.component('ModalDialog', ModalDialog)
```

Example:

```html
<template>
  <section class="container">
    <button class="btn btn-primary" @click="show=true">モーダル表示</button>
    <modal-dialog :show="show" @close="show=false">
        <template v-slot:header>
          <div>ダイアログ</div>
        </template>
        <template v-slot:body>
          <div>内容</div>
        </template>
        <template v-slot:footer>
          <button class="btn btn-primary" @click="onStore">ＯＫ</button>
          <button class="btn btn-secondary" @click="show=false">キャンセル</button>
        </template>
    </modal-dialog>
  </section>
</template>

<style lang="scss" scoped>
</style>

<script>
import ModalDialog from '../src/vue-mg-modal-dialog'
export default {
  data() {
    return {
      show: false,
    }
  },
    methods: {
      onStore: function () {
        alert('ＯＫが押下されました。')
      }
    },
  components: {
    ModalDialog,
  },  
}
</script>
```

## License

MIT
