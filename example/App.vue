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

    <button class="btn btn-primary" @click="show2=true">モーダル表示(フッターなし）</button>
    <modal-dialog :show="show2" hideFooter="true" @close="show2=false">
        <template v-slot:header>
          <div>ダイアログ</div>
        </template>
        <template v-slot:body>
          <div>内容</div>
          <select class="form-control">
            <option>Default select</option>
          </select>
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
      show2: false,
    }
  },
    methods: {
      onStore: function () {
        alert('OKが押されました。')
      }
    },
  components: {
    ModalDialog,
  },  
}
</script>