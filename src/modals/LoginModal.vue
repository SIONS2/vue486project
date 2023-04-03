<script>
import draggable from 'vuedraggable';
let id = 1;

export default {
  name: 'DialNum',
  components: {
    draggable,
  },
  props: {
    show: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      enabled: true,
      dial1: [
        { name: '5', id: 5 },
        { name: '6', id: 6 },
        { name: '7', id: 7 },
        { name: '8', id: 8 },
        { name: '9', id: 9 },
        { name: '0', id: 0 },
        { name: '1', id: 1 },
        { name: '2', id: 2 },
        { name: '3', id: 3 },
        { name: '4', id: 4 },        
      ],
      dial2: [
      { name: '5', id: 5 },
        { name: '6', id: 6 },
        { name: '7', id: 7 },
        { name: '8', id: 8 },
        { name: '9', id: 9 },
        { name: '0', id: 0 },
        { name: '1', id: 1 },
        { name: '2', id: 2 },
        { name: '3', id: 3 },
        { name: '4', id: 4 }, 
      ],
      dial3: [
      { name: '5', id: 5 },
        { name: '6', id: 6 },
        { name: '7', id: 7 },
        { name: '8', id: 8 },
        { name: '9', id: 9 },
        { name: '0', id: 0 },
        { name: '1', id: 1 },
        { name: '2', id: 2 },
        { name: '3', id: 3 },
        { name: '4', id: 4 }, 
      ],
      dial4: [
      { name: '5', id: 5 },
        { name: '6', id: 6 },
        { name: '7', id: 7 },
        { name: '8', id: 8 },
        { name: '9', id: 9 },
        { name: '0', id: 0 },
        { name: '1', id: 1 },
        { name: '2', id: 2 },
        { name: '3', id: 3 },
        { name: '4', id: 4 }, 
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
      this.list = [{ name: 'Edgard', id: id++ }];
      this.dial2 = [{ name: 'Edgard', id: id++ }];
    },
    checkMove(e) {
      window.console.log('Future index: ' + e.draggedContext.futureIndex);
    },
  },
}
</script>

<template>
  <Transition name="modal">
    <div v-if="show" @click="$emit('close')" class="modal-mask">
      <div class="modal-container">
        <div class="dragWrap">
          <draggable
            :list="dial1"
            :disabled="!enabled"
            item-key="name"
            class="list-group"
            ghost-class="ghost"
            :move="checkMove"
            @start="dragging = true"
            @end="dragging = false"
          >
            <template #item="{ element }">
              <div class="list-group-item" :class="{ 'not-draggable': !enabled }">
                {{ element.name }}
              </div>
            </template>
          </draggable>
        </div>
        
        <div class="dragWrap">
          <draggable
            :list="dial2"
            :disabled="!enabled"
            item-key="name"
            class="list-group"
            ghost-class="ghost"
            :move="checkMove"
            @start="dragging = true"
            @end="dragging = false"
          >
            <template #item="{ element }">
              <div class="list-group-item" :class="{ 'not-draggable': !enabled }">
                {{ element.name }}
              </div>
            </template>
          </draggable>
        </div>
        
        <div class="dragWrap">
          <draggable
            :list="dial3"
            :disabled="!enabled"
            item-key="name"
            class="list-group"
            ghost-class="ghost"
            :move="checkMove"
            @start="dragging = true"
            @end="dragging = false"
          >
            <template #item="{ element }">
              <div class="list-group-item" :class="{ 'not-draggable': !enabled }">
                {{ element.name }}
              </div>
            </template>
          </draggable>
        </div>
        
        <div class="dragWrap">
          <draggable
            :list="dial4"
            :disabled="!enabled"
            item-key="name"
            class="list-group"
            ghost-class="ghost"
            :move="checkMove"
            @start="dragging = true"
            @end="dragging = false"
          >
            <template #item="{ element }">
              <div class="list-group-item" :class="{ 'not-draggable': !enabled }">
                {{ element.name }}
              </div>
            </template>
          </draggable>
        </div>
        
        <!-- <button
          class="modal-default-button"
          @click="$emit('close')"
        >OK</button> -->
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
.modal-default-button {
  float: right;
}

</style>
