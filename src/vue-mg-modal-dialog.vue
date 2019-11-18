<template>
    <transition name="modal" appear>
        <div class="modal modal-overlay" :class="{ 'modal-overlay-start': started }" v-if="show" @click.self="$emit('close')">
            <div class="modal-window" :style="style">
                <div class="modal-header bg-primary text-white" v-if="!hideHeader">
                    <slot name="header"/>
                </div>
                <div class="modal-content">
                    <slot name="body"/>
                </div>
                <footer class="modal-footer" v-if="!hideFooter">
                    <slot name="footer">
                        <button class="btn btn-primary" @click="$emit('submit')">ＯＫ</button>
                        <button class="btn btn-secondary" @click="$emit('close')">キャンセル</button>
                    </slot>
                </footer>
            </div>
        </div>
    </transition>
</template>

<script>
export default {
    props: {
        show: {
            defalut: false
        },
        size: {
            default: ''
        },
        hideHeader: {
            type: Boolean,
            default: false
        },
        hideFooter: {
            type: Boolean,
            default: false
        },
        width: {
            defalut: '600px'
        },
        started: {
            type: Boolean,
            default: false
        },
    },
    data () {
        return {
            
        }
    },
    computed: {
        style: function () {
            let width = '600px'
            if (this.size == 'custom') {
                width = this.width
            } else if (this.size == 'sm') {
                width = '400px'
            } else if (this.size == 'lg') {
                width = '800px'
            }
            return {
                width: width,
            }
        },
    },
    methods: {

    }
}
</script>

<style lang="scss" scoped>
.modal {
    &.modal-overlay {
        display: flex;
        align-items: center;
        justify-content: center;
        position: fixed;
        z-index: 30;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.5);
    }

    &.modal-overlay-start {
        display: flex;
        align-items: start;
        justify-content: center;
        position: fixed;
        z-index: 30;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.5);
        padding-top: 30px;
    }

    &-window {
        // width: 500px;
        background: #fff;
        border-radius: 4px;
        overflow: hidden;
    }

    &-header {
        background: #ccc;
        // padding: 10px;
        // text-align: right;
    }

    &-content {
        border-top-right-radius: 0;
        border-top-left-radius: 0;
        border-bottom-right-radius: 0;
        border-bottom-left-radius: 0;
        padding: 10px 20px;
        max-height: calc(100vh - 210px);
        overflow-y: auto;
    }

    &-footer {
        // background: #ccc;
        padding: 10px;
        text-align: right;
    }
}

// オーバーレイのトランジション
.modal-enter-active, .modal-leave-active {
    transition: opacity 0.4s;

    // オーバーレイに包含されているモーダルウィンドウのトランジション
    .modal-window {
        transition: opacity 0.4s, transform 0.4s;
    }
}

// ディレイを付けるとモーダルウィンドウが消えた後にオーバーレイが消える
.modal-leave-active {
    transition: opacity 0.6s ease 0.4s;
}

.modal-enter, .modal-leave-to {
    opacity: 0;

    .modal-window {
        opacity: 0;
        transform: translateY(-20px);
    }
}
</style>