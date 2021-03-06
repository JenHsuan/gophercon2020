<template>
  <div id="sponsor" class="container">
    <LogoTop v-if="$store.state.app.device !== 'mobile'" />
    <div class="background-image">
      <div class="image-wrapper">
        <img
          src="https://gophercon.golang.tw/2020/img/subpage-bg.png"
          srcset="https://gophercon.golang.tw/2020/img/subpage-bg@2x.png 2x, https://gophercon.golang.tw/2020/img/subpage-bg@3x.png 3x"
          class="Group-9"
        />
        <img
          src="https://gophercon.golang.tw/2020/img/graphic-team.png"
          srcset="https://gophercon.golang.tw/2020/img/graphic-team@2x.png 2x, https://gophercon.golang.tw/2020/img/graphic-team@3x.png 3x"
          class="team-1"
        />
      </div>
    </div>
    <div class="content">
      <div class="card-container individual-sponsor">
        <div class="card">
          <h2 class="font-black subtitle">GopherCon 團隊</h2>
          <p
            class="paragraph"
          >GopherCon TW 年會每年皆是許多志工奉獻與時間精神所舉辦；若你對參與 GopherCon 年會的籌備有興趣，歡迎填寫表單，我們將在活動開始籌備時通知您！</p>
          <p class="paragraph">
            <a
              href="https://docs.google.com/forms/d/e/1FAIpQLSffrFjdHDGWtU9GWlXhYGzWX-vjUjmHv2bA4imHFe_Lpj7COQ/viewform"
              class="tone-trans form-link font-bold"
              target="_blank"
              rel="noopener"
            >點我寫表單</a>
          </p>
        </div>
      </div>
      <div class="sponsor-wrapper">
        <div v-for="group in staffs" :key="`staff-group-${group.name}`" class="sponsor-card">
          <h2 class="sponsor-name">
            <span>{{ group.name }}</span>
          </h2>
          <div class="sponsor-text-container">{{ group.description }}</div>
          <div class="staff-wrapper">
            <div
              v-for="member in group.members"
              :key="`${group.name}-${member.name}`"
              class="staff"
            >
              <StaffInfo :member="member"></StaffInfo>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

import staffData from '@/../public/json/staff.json';

import LogoTop from '../components/LogoTop.vue';
import StaffInfo from '../components/Team/StaffInfo.vue';

@Component({
  components: {
    LogoTop,
    StaffInfo
  }
})
export default class TeamPage extends Vue {
  private staffs = staffData;
}
</script>

<style lang="scss" scoped>
@import '@/assets/scss/mixin.scss';
@import '@/assets/scss/variables.scss';

$logo-margin-bottom: 20px;

#sponsor {
  min-width: 375px;
  width: 100%;
  font-family: SourceHanSansTW;

  @include for-size(xs) {
    padding-top: calc(
      #{$navbar-height-mobile} + 36px + 84px + #{$logo-margin-bottom}
    );
  }
  @include for-size(sm) {
    padding-top: calc(
      #{$navbar-height-mobile} + 36px + 100px + #{$logo-margin-bottom}
    );
  }
  @include for-size(md) {
    padding-top: calc(
      #{$navbar-height-mobile} + 36px + 153px + #{$logo-margin-bottom}
    );
  }
  @include for-size(lg) {
    padding-top: calc(#{$navbar-height} + 28px + 153px + 20px);
  }
  @include for-size(xl) {
    padding-top: calc(#{$navbar-height} - 32px + 153px + 20px);
  }

  .background-image {
    position: fixed;
    background-color: #fff;
    height: calc(100vw / 16 * 9);
    width: 100vw;
    top: 0;
    left: 0;
    z-index: 0;
    transform-origin: 0 0;
    margin-top: $navbar-height-mobile;
    z-index: -10;

    @include for-size(lg) {
      margin-top: $navbar-height;
    }

    .image-wrapper {
      position: relative;
    }

    .Group-9 {
      &-container {
        position: relative;
        width: 100%;
        height: 100%;
      }

      width: 100%;
      height: auto;
    }

    .team-1 {
      position: absolute;
      right: 0;
      bottom: 0;
    }
  }

  .content {
    margin-left: auto;
    margin-right: auto;
    padding-bottom: 40px;

    @include for-size(md) {
      width: 688px;
    }
    @include for-size(lg) {
      width: 716px;
    }
    @include for-size(xl) {
      width: 716px;
    }
  }
}

.card-container.individual-sponsor {
  font-family: SourceHanSansTW;
  margin-bottom: 40px;

  @include for-size(xs) {
    padding: 0 16px;
  }
  @include for-size(sm) {
    padding: 0 16px;
  }
  @include for-size(md) {
    padding: 0 68px;
  }
  @include for-size(lg) {
    padding: 0 82px;
  }
  @include for-size(xl) {
    padding: 0 82px;
  }

  h2.subtitle {
    margin-bottom: 24px;
    text-align: center;
    font-size: 24px;
    font-weight: 900;
    font-stretch: normal;
    font-style: normal;
    line-height: normal;
    letter-spacing: normal;
    color: #44484f;
  }

  p {
    margin-bottom: 20px;
    font-size: 18px;
    font-weight: normal;
    font-stretch: normal;
    font-style: normal;
    line-height: normal;
    letter-spacing: normal;
    color: #343942;
  }
}

.sponsor-wrapper {
  background-color: #f7f8f9;
  padding-top: 40px;
  padding-bottom: 40px;

  @include for-size(xs) {
    margin-left: 16px;
    margin-right: 16px;
    padding-left: 24px;
    padding-right: 24px;
  }
  @include for-size(sm) {
    margin-left: 16px;
    margin-right: 16px;
    padding-left: 24px;
    padding-right: 24px;
  }
  @include for-size(md) {
    margin-left: 0px;
    margin-right: 0px;
    padding-left: 68px;
    padding-right: 68px;
  }
  @include for-size(lg) {
    margin-left: 0px;
    margin-right: 0px;
    padding-left: 82px;
    padding-right: 82px;
  }
  @include for-size(xl) {
    padding-left: 82px;
    padding-right: 82px;
  }

  > .sponsor-card:not(:last-child) {
    margin-bottom: 40px;
  }

  h2.sponsor-name {
    margin-bottom: 8px;

    span {
      font-size: 24px;
      font-weight: 900;
      font-stretch: normal;
      font-style: normal;
      line-height: normal;
      letter-spacing: normal;
      color: #7bd6eb;

      &.sponsor-level {
        font-size: 14px;
      }
    }
  }

  .staff-wrapper {
    margin-bottom: 40px;

    .staff {
      display: inline-block;
      margin-right: 24px;
      margin-bottom: 24px;

      @include for-size(md) {
        &:nth-child(4n) {
          margin-right: 0;
        }
      }
    }
  }

  .sponsor-text-container {
    margin-bottom: 24px;
    font-size: 14px;
    font-weight: normal;
    font-stretch: normal;
    font-style: normal;
    line-height: 1.71;
    letter-spacing: normal;
    color: #333943;
  }
}
</style>
