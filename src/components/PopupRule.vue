<template>
  <div class="wrapper-popup" v-bind:class="getClassPopup">
    
    <div class="rule">
      <h3>Luật chơi</h3>
      <p>adsjkfjjlljljaljljfls</p>
      <button 
      v-on:click="confirm"
      class="confirm">Đã hiểu</button>
    </div>
    
  </div>
</template>

<script>
export default {
  name: "Popup-rule",
  props: {
      isOpenPopup: {Boolean, default: false},
  },
  data() {
    return {};
  },
  methods: {
      confirm() {
          console.log('confirm PopupRule.vue');
          this.$emit('handleConfirm')
          // truyền event ra App.vue
      }
  },
  computed: {
      getClassPopup: function(){
          return {
              'open-popup': this.isOpenPopup,
          }
      }
  }
};
</script>

<style>
.wrapper-popup {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.4);
  opacity: 0;
  visibility: hidden;
}
.wrapper-popup.open-popup {
  opacity: 1;
  visibility: visible;
  transition: all 0.3s ease;
}
.rule {
  position: absolute;
  font-family: Arial, Helvetica, sans-serif;
  background-color: white;
  width: 350px;
  padding: 20px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%) scale(1.2);
  transition: all 0.3s ease;
}
.open-popup .rule {
  transform: translate(-50%, -50%) scale(1);
}
.rule h3 {
  margin-bottom: 10px;
}
.rule .confirm {
  cursor: pointer;
  margin-top: 20px;
  border: 2px solid black;
  background-color: white;
  padding: 8px 15px;
  transition: all 0.3s ease;
}
.rule .confirm:hover {
  color: white;
  background-color: black;
}
/* kết hợp CSS với VueJS để xây dựng hiệu ứng - Zoom in - Zoom Out */
</style>
