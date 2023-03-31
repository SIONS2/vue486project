<script setup>
import Modal from '../modals/LoginModal.vue'
import { ref } from 'vue'

const showModal = ref(false)
console.log(showModal)
</script>

<template>
  <div class="DiaryLogin">
    <!-- <div id="show-modal" class="lock" @click="showModal = true"><font-awesome-icon :icon="['fas', 'lock']" /></div> -->
    <div class="diaryLockWrap">
        <div class="diaryLock" id="show-modal" @click="showModal = true">
            <ul class="dialNum">
                <li class="dragWrap">0</li>    
                <li class="dragWrap">0</li>
                <li class="dragWrap">0</li>
            </ul>
            <Teleport to="body">
                <modal :show="showModal" @close="showModal = false">
                    <template #header>
                        <h3>custom header</h3>
                    </template>       
                </modal>
            </Teleport>
        </div>
    </div>
    <div class="DiaryTitle">
        486Diary
    </div>
    <div class="imgArea">
        <img src="@/assets/images/mainImg.png" alt="메인이미지"/>
    </div>
    <div class="copyright">@2021.06.26</div>
  </div>
</template>

<style>
.main_bg_inner:has(.DiaryLogin){
    width:90% !important;
    height:70% !important;
    border-radius: 0px !important;
    position:relative;
}
.DiaryLogin{
    width: 100%;
    height: 100%;
}
/*다이어리 잠금 표시 영역*/
.diaryLockWrap{
    position: absolute;
    right: 0;
    top: 50%;
    transform: translateY(-50%);
    background-color: var(--color-inner-bg);
    width: 40%;
    height: 60px;
    border-top-left-radius: var(--radius-lock);
    border-bottom-left-radius: var(--radius-lock);
}
.diaryLock {
    width: 70%;
    height: 100%;
    background-color: var(--radius-lock);
    cursor: pointer;
}
.dialNum {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    box-sizing: border-box;
    padding: 0 10px;
}
.dragWrap {
    font-size: 35px;
    font-weight: bold;
    width: 33.3333%;
    text-align: center;
}
/*다이어리 표지*/
.DiaryTitle{
    width: 50%;
    height: 10%;
    font-size: 36px;
    display: flex;
    align-items: center;
    font-weight: bold;
    border-bottom: 1px solid #000;
    margin-left: 15px;
    box-sizing: border-box;
    letter-spacing: 5px;
}
.imgArea{
    width: 100%;
    height: 80%;
    padding: 15px;
    box-sizing:border-box;
}
.copyright{
    width: 100%;
    height: 10%;
    display:flex;
    align-items:start;
    justify-content:center;
    font-weight:bold;
}
</style>