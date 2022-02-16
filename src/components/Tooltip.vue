<template>
  <q-tooltip
    @show="onShow"
    ref="tooltipRef"
    class="tooltip"
    :class="`tooltip-arrow-${ arrowClass }`"
  >
    <div
      class="tooltip-text text-body1 text-bold relative-position"
      :class="`bg-${ bgColor } text-${ color }`"
    >
      <slot/>
      <q-btn
        @click.prevent="closeTooltip"
        v-if="closeable"
        icon="close"
        class="tooltip-close absolute-top-right"
        size="sm"
        dense
        round
      />
    </div>
    <div
      class="tooltip-arrow absolute"
      :class="`bg-${ bgColor }`"
    />
  </q-tooltip>
</template>

<script>
  import { computed, ref } from 'vue'

  export default {
    props: {
      arrow: {
        type: String,
        default: 'top'
      },
      duration: {
        type: Number,
        default: null
      },
      closeable: {
        type: Boolean,
        default: null
      },
      bgColor: {
        type: String,
        default: 'grey-10'
      },
      color: {
        type: String,
        default: 'white'
      },
    },
    setup(props) {
      /*
       reusables
     */
      const tooltipRef = ref(null)



      /*
        arrow class
      */

      const arrowClass = computed(() => {
        let arrowClassCorrected = props.arrow.replace(' ', '-')
        let allowedClasses =
          [
            'top', 'top-left', 'top-right',
            'bottom', 'bottom-left', 'bottom-right',
            'right', 'right-top', 'right-bottom',
            'left', 'left-top', 'left-bottom',
          ]
        if (!allowedClasses.includes(arrowClassCorrected)) {
          console.error(`Value "${ arrowClassCorrected }" is not allowed for "arrow" prop. Use one of these (with or without dashes): `, allowedClasses)
          return 'top'
        }
        return arrowClassCorrected
      })

      /*
        event-onShow
      */
      const onShow = () => {
        if (props.duration) {
          setTimeout(() => {
            tooltipRef.value.hide()
          }, props.duration)
        }
      }


      /*
        close tooltip
      */
      const closeTooltip = () => {
        tooltipRef.value.hide()
      }


      /*
        return
      */
      return {
        arrowClass,
        tooltipRef,
        onShow,
        closeTooltip,
      }
    }

  }
</script>

<style lang="scss">

  $box-shadow: 0 0 30px 0 rgba(0,0,0,0.5);

  .tooltip {
    overflow: visible;
    background: transparent;
    box-shadow: $box-shadow;
    padding: 0;
    border-radius: 10px;

    &-text {
      z-index: 10;
      padding: 20px;
      border-radius: 10px;
    }

    &-arrow {
      z-index: 5;
      box-shadow: $box-shadow;
      width: 30px;
      height: 30px;
      transform: translateX(-50%) rotate(-45deg) skew(-20deg, -20deg);

      // top arrows

      [class*="tooltip-arrow-top"] & {
        top: 0;
      }

      .tooltip-arrow-top & {
        left: 50%;
      }

      .tooltip-arrow-top-left & {
        left: 20%;
      }

      .tooltip-arrow-top-right & {
        right: 0;
      }

      // bottom arrows

      [class*="tooltip-arrow-bottom"] & {
        bottom: 0;
      }

      .tooltip-arrow-bottom & {
        left: 50%;
      }

      .tooltip-arrow-bottom-left & {
        left: 20%;
      }

      .tooltip-arrow-bottom-right & {
        right: 0;
      }

      // left arrows

      [class*="tooltip-arrow-left"] & {
        transform: translateY(-50%) rotate(45deg) skew(-20deg, -20deg);
      }

      .tooltip-arrow-left & {
        top: 50%;
        left: 0;
      }

      .tooltip-arrow-left-top & {
        top: 20px;
      }

      .tooltip-arrow-left-bottom & {
        bottom: -10px;
      }

      // right arrows

      [class*="tooltip-arrow-right"] & {
        transform: translateY(-50%) rotate(45deg) skew(-20deg, -20deg);
        right: 0;
      }

      .tooltip-arrow-right & {
        top: 50%;
      }

      .tooltip-arrow-right-top & {
        top: 20px;
      }

      .tooltip-arrow-right-bottom & {
        bottom: -10px;
      }
    }

    &-close {
      pointer-events: all;
    }
  }

</style>
