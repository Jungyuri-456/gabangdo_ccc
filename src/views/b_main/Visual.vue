<template>
  <div class="ma_visual-wrap">
    <div class="inner">
      <!-- 오른쪽 -->
      <div class="mavisimg">
        <!-- <img src="/images/ma/ma_visual/mavisual.gif" alt="ma-viusal" /> -->
        <img src="/images/gh/ma_visual/mavisual.gif" alt="메인비쥬얼" />
      </div>
    </div>
  </div>
</template>
<script setup></script>
<style lang="scss" scoped>
@use "/src/assets/Variables" as *;
/* 전체영역 */
.ma_visual-wrap .inner {
  width: 100%;
  max-width: 800px;;
  display: flex;
  justify-content: center;
  margin: 50px auto 80px;
  /* background-color: antiquewhite; */
}
/* 왼쪽 - 텍스트박스  */
.mavistxt {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 25%;
  img {
    margin-top: 180px;
    width: 100%;
    padding: 20px 20px 50px;   
  }
}
.ma_vis_h1 h1:first-child {
  font-size: 20px !important;
  line-height: 30px !important;
  /* text-align: center; */
}
.mavistxt > h4 {
  width: 300px;
  font-size: 16px;
  color: #5a5a5a;
  margin-bottom: 10px;
}
.mavistxt > h1,
.ma_vis_h1 h1 {
  font-size: 40px;
  color: #5a5a5a;
  line-height: 50px;
}
.ma_vis_h1 {
  display: flex;
  justify-content: right;
  gap: 10px;
}
/* 맡기세요! (문구- 블루) */
.mablue {
  width: 230px;
  color: #0066b3 !important;
  padding: 20px 0 !important;
}
.mavistxt > button {
  position: relative;
  width: 145px;
  line-height: 60px;
  font-size: 19px;
  // background: #0066b3;
  background: #db27b1;
  border: none;
  border-radius: $border-radius-L + $border-radius-s;
  a {
    color: white !important;
  }  
  cursor: pointer;
  transition: 0.3s;
  text-align: center;
  span {
    font-size: 21px;
    margin-left: 5px;
  }
}
.mavistxt > button:hover {
  background: #e961c9;
}
/* 오른쪽 - gif이미지 */
.mavisimg {
  position: relative;
  width: 70%;
  /* min-width: 390px; */
}
.mavisimg > img {
  width: 100%;
  padding: 0px 0px 50px 0px;
}
audio {
  width: 100%;
  max-width: 100px; /* 적절한 크기로 제한 */
  height: 30px;
  background-color: #fff !important; /* 배경색 변경 */
  border-radius: 10px; /* 둥근 모서리 */
  position: absolute;
  bottom: 50px;
  right: 0px;
}
</style>
