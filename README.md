# vue-mg-modal-dialog


![npm](https://img.shields.io/npm/v/vue-mg-modal-gialog)
![npm](https://img.shields.io/npm/dm/vue-mg-modal-gialog)

## Installation

```
npm i vue-mg-modal-gialog
```

## Usage

app.js

```javascript
import ModalDialog from 'vue-mg-modal-gialog'
Vue.component('ModalDialog', ModalDialog)
```

Example:

```html
<template>
  <section class="container">
    <button class="btn btn-primary" @click="show=true">���[�_���\��</button>
    <modal-dialog :show="show" @close="show=false">
        <template v-slot:header>
          <div>�_�C�A���O</div>
        </template>
        <template v-slot:body>
          <div>���e</div>
        </template>
        <template v-slot:footer>
          <button class="btn btn-primary" @click="onStore">�n�j</button>
          <button class="btn btn-secondary" @click="show=false">�L�����Z��</button>
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
        alert('OK��������܂����B')
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
