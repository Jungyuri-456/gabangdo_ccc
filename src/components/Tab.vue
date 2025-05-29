<script setup>
import { ref, computed, onMounted, onUnmounted } from "vue";
// 탭키 내용
const activeTab = ref("subway");
// 창 너비 추적
const windowWidth = ref(window.innerWidth);
function onResize() {
  windowWidth.value = window.innerWidth;
}
onMounted(() => window.addEventListener("resize", onResize));
onUnmounted(() => window.removeEventListener("resize", onResize));

// 컨테이너 폭: 1100px 초과 시 1100px, 이하 시 100%
const containerStyle = computed(() => ({
  width: windowWidth.value > 1100 ? "1100px" : "100%",
  maxWidth: "1100px",
  height: "auto",
  margin: "0 auto",
}));

// 제목
const tabsTitle = [
  "대구지하철 1호선",
  "대구지하철 2호선",
  "대구 기차역",
  "대구 국제공항",
];
// 소제목
const tabsSubTitle = ["장소", "위치", "보관함 수"];
// 내용들
// 지하철1호선 1번째
const storageData = ref([
  { station: "반월당역", location: "1호선출구 14-2번", count: 38 },
  { station: "중앙로역 A", location: "1번 출구 방향 지하1층", count: 14 },
  { station: "중앙로역 B", location: "대한프라임빌딩 계단 밑", count: 14 },
  { station: "중앙로역 D", location: "육상사거리 옆", count: 29 },
  { station: "중앙로역 E", location: "지하1층 3번 출구", count: 14 },
  { station: "중앙로역 F", location: "지하1층 반곡 공구", count: 34 },
  { station: "대구역", location: "GS25 옆", count: 14 },
  { station: "봉산시장역", location: "과일 가게 옆 출구", count: 7 },
  { station: "신남역", location: "화장실 옆 1,2번 출구", count: 14 },
  { station: "동대구역 A", location: "다이소 옆벽면", count: 14 },
]);
// 지하철1호선 2번째
const storageData2 = ref([
  { station: "동대구역 B", location: "다이소 오픈편", count: 14 },
  { station: "동대구역쇼룸 A", location: "1번출구방향", count: 29 },
  { station: "동대구역쇼룸 B", location: "1번출구방향", count: 26 },
  { station: "중구청역", location: "쓰리야삼겹 옆 2,3번출구", count: 36 },
  { station: "이월드역", location: "육삼냉면 1,4번 출구", count: 38 },
  { station: "반고개역", location: "육삼냉면 2,3번 출구", count: 38 },
  { station: "한성미술학원", location: "1,2번 출구 방향", count: 38 },
]);
// 지하철2호선 1번째
const storageData3 = ref([
  { station: "범어네거리 A", location: "지하3층 만남의 광장", count: 34 },
  { station: "범어네거리 B", location: "A에 보이면", count: 36 },
  { station: "범어네거리 C", location: "지하3층 14-1번 방향", count: 47 },
  { station: "경대병원역", location: "2,3 이마트 2층", count: 14 },
  { station: "대구은행역", location: "1,4번 출구 방향", count: 14 },
  { station: "범어역", location: "에스에스패션 앞", count: 14 },
  { station: "수성구청역", location: "1,4번 출구 방향", count: 14 },
  { station: "만촌역", location: "1,4번 출구 방향", count: 14 },
  { station: "대공원역", location: "2,3번 출구 방향", count: 41 },
  { station: "신매역", location: "1,7번 출구 방향", count: 14 },
]);
// 지하철2호선 2번째
const storageData4 = ref([
  { station: "사월역", location: "2번 출구 방향", count: 14 },
  { station: "염산역(임시칭)", location: "3,4번 출구 방향", count: 7 },
  { station: "범어역 C", location: "지하3층 14-1번 방향", count: 47 },
  { station: "경대병원역", location: "2,3 이마트 2층", count: 14 },
  { station: "대구은행역", location: "1,4번 출구 방향", count: 14 },
  { station: "범어역", location: "역시그렇게 나와있음", count: 14 },
  { station: "수성구청역", location: "1,4번 출구 방향", count: 14 },
  { station: "만촌역", location: "1,4번 출구 방향", count: 14 },
  { station: "대공원역", location: "2,3번 출구 방향", count: 14 },
  { station: "신매역", location: "1,7번 출구 방향", count: 14 },
]);
// 대구 기차역
const storageData5 = ref([
  { station: "대구역", location: "1층 화장실 옆", count: 40 },
  { station: "동대구역", location: "마트소 앞", count: 40 },
  { station: "서대구역", location: "편의점 맞은편", count: 30 },
]);
// 대구 공항
const storageData6 = ref([
  {
    station: "대구 국제공항",
    location: `대구국제공항 입국장
근처 사물함 (도착층)`,
    count: 60,
  },
]);

// 스와이퍼 사용
import { Swiper, SwiperSlide } from "swiper/vue";
import { Pagination } from "swiper/modules";

// Swiper 스타일
import "swiper/css";
import "swiper/css/pagination";
</script>

<template>
  <div class="bb_StoreTable" :style="containerStyle">
    <!-- tab키 -->
    <div class="bb_StoreTabs">
      <div class="bb_buttonBorder">
        <!-- 버튼3개 -->
        <!-- 지하철버튼 -->
        <button
          @click="activeTab = 'subway'"
          :class="{ active: activeTab === 'subway' }"
        >
          지하철
        </button>
        <!-- 기차역버튼 -->
        <button
          @click="activeTab = 'train'"
          :class="{ active: activeTab === 'train' }"
        >
          기차역
        </button>
        <!-- 공항버튼 -->
        <button
          @click="activeTab = 'airport'"
          :class="{ active: activeTab === 'airport' }"
        >
          공항
        </button>
      </div>
    </div>
    <!-- 테이블 내용 -->
    <!-- tab1 -->
    <div class="bb_StoreContents">
      <div class="bb_StoreContent1" v-if="activeTab === `subway`">
        <Swiper
          :modules="[Pagination]"
          :pagination="{ clickable: true }"
          :slides-per-view="1"
          :space-between="30"
          class="bb_mySwiper"
        >
          <!-- 슬라이드 1 -->
          <SwiperSlide>
            <div class="bb_slide1">
              <h1 class="bb_tabTitle">{{ tabsTitle[0] }}</h1>

              <table class="tabContent1">
                <thead class="bb_tabSubtitle">
                  <tr>
                    <th v-for="(subtitle, index) in tabsSubTitle" :key="index">
                      {{ subtitle }}
                    </th>
                  </tr>
                </thead>
                <tbody>
                  <tr
                    class="bb_contentS"
                    v-for="(item, i) in storageData"
                    :key="i"
                  >
                    <td>
                      <div class="bb_cell">{{ item.station }}</div>
                    </td>
                    <td>
                      <div class="bb_cell">{{ item.location }}</div>
                    </td>
                    <td>
                      <div class="bb_cell">{{ item.count }}</div>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </SwiperSlide>

          <!-- 슬라이드 2 -->
          <SwiperSlide>
            <div class="bb_slide1">
              <h1 class="bb_tabTitle">{{ tabsTitle[0] }}</h1>

              <table class="tabContent1">
                <thead class="bb_tabSubtitle">
                  <tr>
                    <th v-for="(subtitle, index) in tabsSubTitle" :key="index">
                      {{ subtitle }}
                    </th>
                  </tr>
                </thead>
                <tbody>
                  <tr
                    class="bb_contentS"
                    v-for="(item, i) in storageData2"
                    :key="i"
                  >
                    <td>
                      <div class="bb_cell">{{ item.station }}</div>
                    </td>
                    <td>
                      <div class="bb_cell">{{ item.location }}</div>
                    </td>
                    <td>
                      <div class="bb_cell">{{ item.count }}</div>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </SwiperSlide>

          <!-- 슬라이드 3 -->
          <SwiperSlide>
            <div class="bb_slide1">
              <h1 class="bb_tabTitle2">{{ tabsTitle[1] }}</h1>

              <table class="tabContent1">
                <thead class="bb_tabSubtitle">
                  <tr>
                    <th v-for="(subtitle, index) in tabsSubTitle" :key="index">
                      {{ subtitle }}
                    </th>
                  </tr>
                </thead>
                <tbody>
                  <tr
                    class="bb_contentS"
                    v-for="(item, i) in storageData3"
                    :key="i"
                  >
                    <td>
                      <div class="bb_cell">{{ item.station }}</div>
                    </td>
                    <td>
                      <div class="bb_cell">{{ item.location }}</div>
                    </td>
                    <td>
                      <div class="bb_cell">{{ item.count }}</div>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </SwiperSlide>

          <!-- 슬라이드 4-->
          <SwiperSlide>
            <div class="bb_slide1">
              <h1 class="bb_tabTitle2">{{ tabsTitle[1] }}</h1>

              <table class="tabContent1">
                <thead class="bb_tabSubtitle">
                  <tr>
                    <th v-for="(subtitle, index) in tabsSubTitle" :key="index">
                      {{ subtitle }}
                    </th>
                  </tr>
                </thead>
                <tbody>
                  <tr
                    class="bb_contentS"
                    v-for="(item, i) in storageData4"
                    :key="i"
                  >
                    <td>
                      <div class="bb_cell">{{ item.station }}</div>
                    </td>
                    <td>
                      <div class="bb_cell">{{ item.location }}</div>
                    </td>
                    <td>
                      <div class="bb_cell">{{ item.count }}</div>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </SwiperSlide>

          <!-- 슬라이드 5-->
          <SwiperSlide>
            <div class="bb_slide1">
              <h1 class="bb_tabTitle2">{{ tabsTitle[1] }}</h1>

              <table class="tabContent1">
                <thead class="bb_tabSubtitle">
                  <tr>
                    <th v-for="(subtitle, index) in tabsSubTitle" :key="index">
                      {{ subtitle }}
                    </th>
                  </tr>
                </thead>
                <tbody>
                  <tr
                    class="bb_contentS"
                    v-for="(item, i) in storageData5"
                    :key="i"
                  >
                    <td>
                      <div class="bb_cell">{{ item.station }}</div>
                    </td>
                    <td>
                      <div class="bb_cell">{{ item.location }}</div>
                    </td>
                    <td>
                      <div class="bb_cell">{{ item.count }}</div>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </SwiperSlide>
        </Swiper>
      </div>
      <!-- tab2 -->
      <div class="bb_trainContent2" v-if="activeTab === `train`">
        <Swiper
          :modules="[Pagination]"
          :pagination="{ clickable: true }"
          :slides-per-view="1"
          :space-between="30"
          class="bb_mySwiper"
        >
          <!-- 슬라이드 4-->
          <SwiperSlide>
            <div class="bb_slide1">
              <h1 class="bb_tabTitle3">{{ tabsTitle[2] }}</h1>

              <table class="tabContent1">
                <thead class="bb_tabSubtitle">
                  <tr>
                    <th v-for="(subtitle, index) in tabsSubTitle" :key="index">
                      {{ subtitle }}
                    </th>
                  </tr>
                </thead>
                <tbody>
                  <tr
                    class="bb_contentS"
                    v-for="(item, i) in storageData5"
                    :key="i"
                  >
                    <td>
                      <div class="bb_cell">{{ item.station }}</div>
                    </td>
                    <td>
                      <div class="bb_cell">{{ item.location }}</div>
                    </td>
                    <td>
                      <div class="bb_cell">{{ item.count }}</div>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </SwiperSlide>
        </Swiper>
      </div>
      <!-- tab3 -->
      <div class="bb_trainContent3" v-if="activeTab === `airport`">
        <Swiper
          :modules="[Pagination]"
          :pagination="{ clickable: true }"
          :slides-per-view="1"
          :space-between="30"
          class="bb_mySwiper"
        >
          <!-- 슬라이드 4-->
          <SwiperSlide>
            <div class="bb_slide1">
              <h1 class="bb_tabTitle4">{{ tabsTitle[3] }}</h1>

              <table class="tabContent1">
                <thead class="bb_tabSubtitle">
                  <tr>
                    <th v-for="(subtitle, index) in tabsSubTitle" :key="index">
                      {{ subtitle }}
                    </th>
                  </tr>
                </thead>
                <tbody>
                  <tr
                    class="bb_contentS"
                    v-for="(item, i) in storageData6"
                    :key="i"
                  >
                    <td>
                      <div class="bb_cell">{{ item.station }}</div>
                    </td>
                    <td>
                      <div class="bb_cell">{{ item.location }}</div>
                    </td>
                    <td>
                      <div class="bb_cell">{{ item.count }}</div>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </SwiperSlide>
        </Swiper>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use "/src/assets/_Variables.scss" as *;

// 테이블
.bb_StoreTable {
  width: 100%;
  margin: 0 auto;
  background-color: #fff;
  border: $main-color 1px solid;
  border-radius: $radius;
  overflow: hidden;
  .bb_StoreTabs {
    position: relative;
    height: 70px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: $main-color;
    padding: 0;
    position: relative;
    .bb_buttonBorder {
      flex: 0 0 30%;
      margin: 0 auto;
      width: 30% !important;
      height: 80% !important;
      padding: 5px;
      background-color: #fff;
      border-radius: 50px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      button {
        background-color: #fff;
        color: #000000;
        border-radius: 50px;
        line-height: 30px;
        text-align: center;
        border: none;
        flex: none;
        padding: 0.5rem 1rem;
        margin-top: 2%;
        margin-bottom: 2%;
        cursor: pointer;
        font-size: 20px;
        font-weight: bold;
      }
      button.active {
        background-color: $main-color;
        color: #fff;
      }
    }
  }
  // 테이블내용
  .bb_StoreContents {
    width: 100%;
    height: auto;
    .bb_StoreContent1 {
      width: 100%;
      height: 100%;
      .bb_slide1 {
        width: 100%;
        padding: 30px 10%;
        .bb_tabTitle {
          font-size: 26px;
          color: #ff5c00;
          font-weight: bold;
          padding-bottom: 15px;
        }
        .bb_tabTitle2 {
          font-size: 26px;
          color: #159817;
          font-weight: bold;
          padding-bottom: 15px;
        }
        .tabContent1 {
          width: 100%;
          border-collapse: separate;
          border-spacing: 0 15px; // 이게 핵심!
          .bb_tabSubtitle {
            tr {
              th {
                font-size: 20px;
                font-weight: bold;
                text-align: center;
              }
            }
            .bb_contentS {
              margin-bottom: 10px;
              .bb_cell {
                padding-bottom: 100px;
                background-color: rgba(255, 0, 0, 0.2);
              }
            }
          }
        }
      }
    }
    .bb_trainContent2 {
      width: 100%;
      height: 100%;
      .bb_slide1 {
        width: 100%;
        padding: 30px 10%;
        .bb_tabTitle {
          font-size: 26px;
          color: #ff5c00;
          font-weight: bold;
          padding-bottom: 2%;
        }
        .bb_tabTitle2 {
          font-size: 26px;
          color: #159817;
          font-weight: bold;
          padding-bottom: 2%;
        }
        .bb_tabTitle3 {
          font-size: 26px;
          color: #0066b3;
          font-weight: bold;
          padding-bottom: 2%;
        }
        .tabContent1 {
          width: 100%;
          border-collapse: separate;
          border-spacing: 0 15px; // 이게 핵심!
          .bb_tabSubtitle {
            tr {
              th {
                font-size: 20px;
                font-weight: bold;
                text-align: center;
              }
            }
            .bb_contentS {
              .bb_cell {
                padding-bottom: 100px;
                background-color: rgba(255, 0, 0, 0.2);
              }
            }
          }
        }
      }
    }
    .bb_trainContent3 {
      width: 100%;
      height: 100%;
      .bb_slide1 {
        width: 100%;
        padding: 30px 10%;
        .bb_tabTitle {
          font-size: 26px;
          color: #ff5c00;
          font-weight: bold;
          padding-bottom: 2%;
        }
        .bb_tabTitle2 {
          font-size: 26px;
          color: #159817;
          font-weight: bold;
          padding-bottom: 2%;
        }
        .bb_tabTitle3 {
          font-size: 26px;
          color: #0066b3;
          font-weight: bold;
          padding-bottom: 2%;
        }
        .bb_tabTitle4 {
          font-size: 26px;
          color: #2aaae2;
          font-weight: bold;
          padding-bottom: 2%;
        }
        .tabContent1 {
          width: 100%;
          border-collapse: separate;
          border-spacing: 0 15px; // 이게 핵심!
          .bb_tabSubtitle {
            tr {
              th {
                font-size: 20px;
                font-weight: bold;
                text-align: center;
              }
            }
            .bb_contentS {
              .bb_cell {
                padding-bottom: 100px;
                background-color: rgba(255, 0, 0, 0.2);
              }
            }
          }
        }
      }
    }
  }
}

// 스와이퍼css
#app {
  height: 100%;
}
html,
body {
  position: relative;
  height: 100%;
}

body {
  background: #eee;
  font-family: Helvetica Neue, Helvetica, Arial, sans-serif;
  font-size: 14px;
  color: #000;
  margin: 0;
  padding: 0;
}

.swiper {
  width: 100%;
  height: 100%;
}

.swiper-slide {
  font-size: 18px;
  background: #fff;
}

.swiper-slide img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
}

// 태블릿 : 768px
@media screen and (max-width: 768px) {
  .bb_StoreTable {
    width: 100%;
    height: 700px;
  }
  .bb_StoreTable .bb_StoreContents {
    height: 600px;
  }
  .bb_tabTitle {
    font-size: 20px !important;
  }
  th {
    font-size: 15px !important;
  }
  .bb_cell {
    font-size: 15px !important;
  }
  button {
    font-size: 15px !important;
  }
}

// 모바일 : 390px
@media screen and (max-width: 390px) {
  .bb_StoreTable {
    width: 100%;
    height: 600px;
  }
  .bb_StoreTable .bb_StoreContents {
    height: 550px;
  }
  .bb_StoreTabs {
    padding-left: 2% !important;
  }
  button {
    font-size: 12px !important;
    padding: 1% !important;
    margin-top: 0.5% !important;
    margin-bottom: 0.5% !important;
  }
}
</style>
