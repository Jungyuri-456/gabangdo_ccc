<template>
  <div class="widthAllBg">
    <div class="blockgr"></div>
    <div class="inner">
      <!-- 그라데이션 구분 -->

      <div class="title">
        <h2>고객님들의</h2>
        <h2>이용후기</h2>
        <router-link to="/Sotong2">
          <button>View More</button>
        </router-link>
        <div class="grayLine"></div>
      </div>
      <swiper
        :slides-per-view="3.5"
        :space-between="30"
        :modules="[Pagination]"
        class="mySwiper">
        <!-- 리뷰카드1 -->
        <swiper-slide>
          <div class="Reviews">
            <!-- 사진 -->
            <div class="cardImg">
              <img src="/public/images/carrier2.png" alt="" />
            </div>
            <!-- 이름 -->
            <div class="name">
              <p>김 * *</p>
            </div>
            <!-- 후기 -->
            <div class="Review">
              <p>출장길 짐때문에 이동이 번거로울 뻔했는데</p>
              <p>지인의 추천으로 써보니 좋았습니다.</p>
            </div>
          </div>
        </swiper-slide>
        <!-- 리뷰카드2 -->
        <swiper-slide>
          <div class="Reviews">
            <!-- 사진 -->
            <div class="cardImg">
              <img src="/public/images/carrier3.png" alt="" />
            </div>
            <!-- 이름 -->
            <div class="name">
              <p>하 * *</p>
            </div>
            <!-- 후기 -->
            <div class="Review">
              <p>부모님 데리고 가족여행을 대구로 왔는데</p>
              <p>짐이 너무 많은거에요!! 덕분에 짐 덜었습니다ㅎㅎ</p>
            </div>
          </div>
        </swiper-slide>
        <!-- 리뷰카드3 -->
        <swiper-slide>
          <div class="Reviews">
            <!-- 사진 -->
            <div class="cardImg">
              <img src="/public/images/carrier5.png" alt="" />
            </div>
            <!-- 이름 -->
            <div class="name">
              <p>권 * *</p>
            </div>
            <!-- 후기 -->
            <div class="Review">
              <p>이번 여행때 차가없어서 고민이 많았는데</p>
              <p>
                친구의 추천으로 알게되었습니다. 한번씩 가벼운 여행을 하고 싶을때
                추천드립니다.
              </p>
            </div>
          </div>
        </swiper-slide>
        <!-- 리뷰카드4 -->
        <swiper-slide>
          <div class="Reviews">
            <!-- 사진 -->
            <div class="cardImg">
              <img src="/public/images/carrier6.png" alt="" />
            </div>
            <!-- 이름 -->
            <div class="name">
              <p>하 * *</p>
            </div>
            <!-- 후기 -->
            <div class="Review">
              <p>부모님 데리고 가족여행을 대구로 왔는데</p>
              <p>짐이 너무 많은거에요!! 덕분에 짐 덜었습니다ㅎ</p>
            </div>
          </div>
        </swiper-slide>
        <!-- 리뷰카드5 -->
        <swiper-slide>
          <div class="Reviews">
            <!-- 사진 -->
            <div class="cardImg">
              <img src="/public/images/carrier4.png" alt="" />
            </div>
            <!-- 이름 -->
            <div class="name">
              <p>우 * *</p>
            </div>
            <!-- 후기 -->
            <div class="Review">
              <p>즐거운여행!!</p>
              <p>가벼운 여행!!</p>
            </div>
          </div>
        </swiper-slide>
        <!-- 리뷰카드6 -->
        <swiper-slide>
          <div class="Reviews">
            <!-- 사진 -->
            <div class="cardImg">
              <img src="/public/images/carrier1.png" alt="" />
            </div>
            <!-- 이름 -->
            <div class="name">
              <p>나 * *</p>
            </div>
            <!-- 후기 -->
            <div class="Review">
              <p>대구 여행길 짐이 많아 고민이었는데</p>
              <p>덕분에 편하게 여행했습니다.</p>
            </div>
          </div>
        </swiper-slide>
      </swiper>
    </div>
  </div>
</template>
<script setup>
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/pagination";
// import '@/style.css';
import { Pagination } from "swiper/modules";
</script>
<style lang="scss" scoped>
@use "/src/assets/Variables" as *;
.widthAllBg {
  margin-top: 150px;
  // .blockgr{
  //       background: linear-gradient(to bottom, #f2f2f2, #ffffff);
  //       height: 70px; // 필요에 따라 조정
  //       margin-top: 90px;
  //     }
  // background: linear-gradient(
  //   to bottom,
  //   #f3f3f3,
  //   #fff
  // ); // 회색(#ccc) → 하얀색(#fff)
  // height: 100vh;

  .inner {
    display: flex;
    max-width: 1200px;
    margin: 0 auto;

    .title {
      width: 35%;
      display: flex;
      flex-direction: column; /* 세로로 쌓이게 */
      align-items: flex-start; /* 왼쪽 정렬 */

      h2 {
        font-size: 35px;
        text-align: center;
        font-family: $font-family;
        padding-bottom: 5px;
      }
      button {
        border: 1px solid #8b8b8b;
        border-radius: 30px;
        font-size: 20px;
        padding: 5px;
        padding-left: 15px;
        padding-right: 15px;
        color: #8b8b8b;
        margin-top: 50px;
      }
      button:hover {
        background-color: #8b8b8b;
        color: #fff;
      }
      .grayLine {
        width: 80px;
        height: 5px;
        background-color: #8b8b8b;
        margin-top: 212px;
      }
    }

    .Reviews {
      width: 100%;
      height: 430px;
      // background-color: #f0f0f0;
      border: 3px solid #f0f0f0;

      padding: 4%;
      border-radius: 15px;
      .cardImg {
        img {
          width: 100%;
          height: 280px;
          border-radius: 5px;
        }
      }
      .name {
        font-size: 24px;
        margin-top: 10px;
        margin-bottom: 10px;
      }
      .Review {
        font-size: 15px;
        p {
          margin-bottom: 3px;
          font-family: $font-ownglyph;
          white-space: nowrap;
          overflow: hidden;
          text-overflow: ellipsis;
        }
      }
    }
  }
}
</style>
