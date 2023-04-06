<script>
import draggable from 'vuedraggable';
let id = 1;

export default {
  /* 모달 */
  props: {
    show: {
      type: Boolean,
      default: false,
    },
  },
  /*draggable 라이브러리*/
  name: 'DialNum',
  components: {
    draggable,
  },
  data() {
    return {
      enabled: true,
      dial1: [
        { dialKey: '5', id: 5 },
        { dialKey: '6', id: 6 },
        { dialKey: '7', id: 7 },
        { dialKey: '8', id: 8 },
        { dialKey: '9', id: 9 },
        { dialKey: '0', id: 0 },
        { dialKey: '1', id: 1 },
        { dialKey: '2', id: 2 },
        { dialKey: '3', id: 3 },
        { dialKey: '4', id: 4 },        
      ],
      dial2: [
        { dialKey: '5', id: 5 },
        { dialKey: '6', id: 6 },
        { dialKey: '7', id: 7 },
        { dialKey: '8', id: 8 },
        { dialKey: '9', id: 9 },
        { dialKey: '0', id: 0 },
        { dialKey: '1', id: 1 },
        { dialKey: '2', id: 2 },
        { dialKey: '3', id: 3 },
        { dialKey: '4', id: 4 }, 
      ],
      dial3: [
        { dialKey: '5', id: 5 },
        { dialKey: '6', id: 6 },
        { dialKey: '7', id: 7 },
        { dialKey: '8', id: 8 },
        { dialKey: '9', id: 9 },
        { dialKey: '0', id: 0 },
        { dialKey: '1', id: 1 },
        { dialKey: '2', id: 2 },
        { dialKey: '3', id: 3 },
        { dialKey: '4', id: 4 }, 
      ],
      dial4: [
        { dialKey: '5', id: 5 },
        { dialKey: '6', id: 6 },
        { dialKey: '7', id: 7 },
        { dialKey: '8', id: 8 },
        { dialKey: '9', id: 9 },
        { dialKey: '0', id: 0 },
        { dialKey: '1', id: 1 },
        { dialKey: '2', id: 2 },
        { dialKey: '3', id: 3 },
        { dialKey: '4', id: 4 }, 
      ],
      dragging: false,
    };
  },
  computed: {
    draggingInfo() {
      return this.dragging ? 'under drag' : '';
    },  
  },
  methods: {   
    replace() {
      this.dial1 = [{ name: 'Edgard', id: id++ }];
      this.dial2 = [{ name: 'Edgard', id: id++ }];
      console.log(this)
    },
    replaceDials(){
      this.$refs.dialNum.replace();
    },
    checkMove(e) {
      window.console.log('Future index: ' + e.draggedContext.futureIndex);
    },
  },
}

</script>

<template>
  <Transition name="modal">
    <div v-if="show" class="modal-mask" @click="$emit('close')">
      <div class="modal-container">

        <!-- <div class="dragWrap"
          v-for="(dial, index) in dials" :key="index"
        >

        </div> -->

        <div class="dragWrap">
          <draggable
            :list="dial1"
            :disabled="!enabled"
            item-key="dialKey"
            class="dial-group"
            ghost-class="ghost"
            :move="checkMove"
            @start="dragging = true"
            @end="dragging = false"
          >
            <template #item="{ element }">
              <div class="dial-group-item" :class="{ 'not-draggable': !enabled }">
                {{ element.dialKey }}
              </div>
            </template>
          </draggable>
        </div>
        
        <div class="dragWrap">
          <draggable
            :list="dial2"
            :disabled="!enabled"
            item-key="dialKey"
            class="dial-group"
            ghost-class="ghost"
            :move="checkMove"
            @start="dragging = true"
            @end="dragging = false"
          >
            <template #item="{ element }">
              <div class="dial-group-item" :class="{ 'not-draggable': !enabled }">
                {{ element.dialKey }}
              </div>
            </template>
          </draggable>
        </div>
        
        <div class="dragWrap">
          <draggable
            :list="dial3"
            :disabled="!enabled"
            item-key="dialKey"
            class="dial-group"
            ghost-class="ghost"
            :move="checkMove"
            @start="dragging = true"
            @end="dragging = false"
          >
            <template #item="{ element }">
              <div class="dial-group-item" :class="{ 'not-draggable': !enabled }">
                {{ element.dialKey }}
              </div>
            </template>
          </draggable>
        </div>
        
        <div class="dragWrap">
          <draggable
            :list="dial4"
            :disabled="!enabled"
            item-key="dialKey"
            class="dial-group"
            ghost-class="ghost"
            :move="checkMove"
            @start="dragging = true"
            @end="dragging = false"
          >
            <template #item="{ element }">
              <div class="dial-group-item" :class="{ 'not-draggable': !enabled }">
                {{ element.dialKey }}
              </div>
            </template>
          </draggable>
        </div>
      </div>
    </div>
  </Transition>
</template>

<style scoped>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  transition: opacity 0.3s ease;
}

.modal-container {
  width: 320px;
  height: 80px;
  margin: auto;
  background-color: #e1d9cd;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  display: flex;
  overflow: hidden;
  box-sizing: border-box;
  padding: 0px 10px;
  justify-content: space-between;
}
.dragWrap {
  width: 23%;
  height: 100%;
  display: flex;
  align-items: center;
  font-size: 50px;
  justify-content: center;
  background-color: #663400;
  padding-bottom: 40px;
  box-sizing: border-box;
  font-weight: bold;
  color: #fff;
}
.dial-group-item{
  -webkit-user-select: none;  /* Chrome all / Safari all */
	-moz-user-select: none;     /* Firefox all */
	-ms-user-select: none;
	transition: box-shadow .45s linear, color .25s linear;
	-webkit-transition: box-shadow .45s linear, color .25s linear;
}

</style>