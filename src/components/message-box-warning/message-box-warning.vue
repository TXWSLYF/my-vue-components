<template>
  <transition name="slide-bottom">
    <div class="message-box-warning" v-show="visible">
      <div class="mask"></div>
      <div class="container">
        <div class="close">
          <img src="./common-close.png" @click="handleClickClose" />
        </div>
        <div class="content">
          <div class="icon">
            <img src="./warning-icon.png" />
          </div>
          <div class="title">{{ title }}</div>
        </div>
        <div class="operate">
          <button @click="handleClickCancel">取消</button>
          <button @click="handleClickOk">
            确定
          </button>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'MessageBoxWarning',
  props: {
    visible: {
      required: true,
      type: Boolean,
    },
    title: {
      required: false,
      default: "",
      type: String,
    },
  },

  methods: {
    handleClickClose() {
      this.$emit("update:visible", false);
    },

    handleClickCancel() {
      this.$emit("cancel");
    },

    handleClickOk() {
      this.$emit("ok");
    },
  },
};
</script>

<style lang="less" scoped>
.slide-bottom-leave-active,
.slide-bottom-enter-active {
  transition: all 0.2s ease-out;
}

.slide-bottom-enter,
.slide-bottom-leave-to {
  opacity: 0;
}

.message-box-warning {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 1001;

  .mask {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(0, 0, 0, 0.6);
  }

  .container {
    position: absolute;
    width: 420px;
    height: 180px;
    background: #ffffff;
    border-radius: 4px;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);

    .close {
      height: 48px;
      padding-right: 17px;
      display: flex;
      align-items: center;
      justify-content: flex-end;

      img {
        width: 14px;
        height: 14px;
        cursor: pointer;
      }
    }

    .content {
      display: flex;
      align-items: center;
      padding-left: 32px;
      margin-top: 8px;

      .icon {
        img {
          width: 32px;
          height: 32px;
        }
      }

      .title {
        margin-left: 16px;
        font-weight: 500;
        color: #333333;
        font-size: 16px;
      }
    }

    .operate {
      box-sizing: border-box;
      position: absolute;
      bottom: 0;
      height: 48px;
      display: flex;
      justify-content: flex-end;
      width: 100%;
      padding-right: 16px;
    }
  }
}
</style>
