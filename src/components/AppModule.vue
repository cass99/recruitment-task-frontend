<template>
  <div class="Module">
    <h2
      v-if="header"
      class="Module__header"
    >
      {{ header }}
    </h2>
    <p
      v-if="subheader"
      class="Module__subheader"
    >
      {{ subheader }}
    </p>

    <div class="Module__items">
      <div
          v-for="(item, index) in module" :key="index"
          :class="{
            'Module__item': true,
            'Module__item--first': index === 0
          }"
      >
        <div
          v-if="item.icon"
          class="Module__itemIcon"
          v-html="item.icon"
        >
        </div>

        <div class="Module__itemTexts">
          <h1
            v-if="item.title"
            class="Module__itemTitle"
          >
            {{ item.title }}
          </h1>
          <p
            v-if="item.text"
            class="Module__itemText"
          >
            {{ item.text }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
  defineProps({
    header: {
      type: String,
      default: null
    },
    subheader: {
      type: String,
      default: null
    },
    module: {
      type: Array,
      default: () => []
    }
  });
</script>

<style scoped lang="scss">
  .Module {
    $self: &;

    padding: 60px 0;

    @include gt-tablet-portrait {
      padding: 120px 0;
    }

    &__ {
      &header {
        text-align: center;
        color: $black;
      }

      &subheader {
        font-size: 14px;
        font-weight: 300;
        text-align: center;

        @include gt-tablet-portrait {
          font-size: 18px;
        }
      }

      &items {
        display: flex;
        flex-direction: column;
        gap: 15px;
        margin-top: 40px;

        @include gt-tablet-portrait {
          margin-top: 60px;
          flex-direction: row;
        }
      }

      &item {
        display: flex;
        flex-direction: column;
        position: relative;
        height: 384px;
        padding: 16px 16px 20px;
        background-color: $surface;
        border-radius: 3px;

        @include gt-tablet-portrait {
          height: 584px;
          padding: 32px 32px 40px;
          width: 22%;
        }

        &--first {
          @include gt-tablet-portrait {
            width: 46%;
          }

          &::after {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            bottom: 0;
            margin: auto;
            width: 100px;
            height: 334px;
            background: url("./src/assets/svg/2-b.svg") no-repeat;
            background-size: contain;

            @include gt-tablet-portrait {
              width: 155px;
              height: 517px;
            }
          }

          #{$self}__ {
            &itemTitle {
              font-size: 100px;

              @include gt-tablet-portrait {
                font-size: 200px;
              }
            }
          }
        }

        &Icon {
          display: flex;
          width: 40px;
          height: 40px;

          @include gt-tablet-portrait {
            width: 48px;
            height: 48px;
          }

          svg {
            width: 100%;
            height: 100%;
          }
        }

        &Texts {
          margin-top: auto;
        }

        &Title {
          color: $black;
        }

        &Text {
          color: $grey;
          letter-spacing: -0.01em;
        }
      }
    }
  }
</style>