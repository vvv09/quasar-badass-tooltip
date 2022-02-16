<template>
  <q-page class="q-pa-md">

    <div class="text-h5">Top Arrows</div>

    <q-btn
      label="Top Arrow (default)"
      no-caps
      color="primary"
      class="q-ma-lg"
    >
      <tooltip>
        I'm so badass
      </tooltip>
    </q-btn>

    <q-btn
      label="Top Left"
      no-caps
      color="primary"
      class="q-ma-lg"
    >
      <tooltip
        arrow="top left"
      >
        I'm so badass
      </tooltip>
    </q-btn>

    <q-btn
      label="Top Right"
      no-caps
      color="primary"
      class="q-ma-lg"
    >
      <tooltip
        arrow="top right"
      >
        I'm so badass
      </tooltip>
    </q-btn>

    <div class="text-h5 q-mt-lg">Bottom Arrows</div>

    <q-btn
      label="Bottom Arrow"
      no-caps
      color="primary"
      class="q-ma-lg"
    >
      <tooltip
        arrow="bottom"
        anchor="top middle"
        self="bottom middle"
      >
        I'm so badass
      </tooltip>
    </q-btn>

    <q-btn
      label="Bottom Left"
      no-caps
      color="primary"
      class="q-ma-lg"
    >
      <tooltip
        arrow="bottom left"
        anchor="top middle"
        self="bottom middle"
      >
        I'm so badass
      </tooltip>
    </q-btn>

    <q-btn
      label="Bottom Right"
      no-caps
      color="primary"
      class="q-ma-lg"
    >
      <tooltip
        arrow="bottom right"
        anchor="top middle"
        self="bottom middle"
      >
        I'm so badass
      </tooltip>
    </q-btn>

    <div class="text-h5 q-mt-lg">Left & Right Arrows</div>

    <q-btn
      label="Left Arrow"
      no-caps
      color="primary"
      class="q-ma-lg"
    >
      <tooltip
        arrow="left"
        anchor="center end"
        self="center start"
      >
        I'm so badass
      </tooltip>
    </q-btn>

    <q-btn
      label="Right Arrow"
      no-caps
      color="primary"
      class="q-ma-lg"
    >
      <tooltip
        arrow="right"
        anchor="center start"
        self="center end"
      >
        I'm so badass
      </tooltip>
    </q-btn>

    <div class="text-h5 q-mt-lg">Programmatically Triggered</div>

    <q-btn
      label="Click to Toggle Tooltip"
      no-caps
      color="primary"
      class="q-ma-lg"
      @click="showTooltip = !showTooltip"
    >
      <tooltip
        v-model="showTooltip"
        no-parent-event
      >
        I'm so badass
      </tooltip>
    </q-btn>

    <q-btn
      label="Hide Tooltip after delay"
      no-caps
      color="primary"
      class="q-ma-lg"
      @click="showTooltipWithHide = true"
    >
      <tooltip
        v-model="showTooltipWithHide"
        no-parent-event
        :duration="2000"
      >
        I'm so badass
      </tooltip>
    </q-btn>

    <q-btn
      label="Tooltip with close button"
      no-caps
      color="primary"
      class="q-ma-lg"
      @click="showTooltipWithClose = true"
    >
      <tooltip
        v-model="showTooltipWithClose"
        no-parent-event
        closeable
      >
        I'm so badass
      </tooltip>
    </q-btn>

    <div class="text-h5 q-mt-lg">Custom Colors!</div>

    <q-btn
      label="White & Black"
      no-caps
      color="primary"
      class="q-ma-lg"
    >
      <tooltip
        bg-color="white"
        color="black"
      >
        I'm so badass
      </tooltip>
    </q-btn>

    <q-btn
      label="White & Pink"
      no-caps
      color="primary"
      class="q-ma-lg"
    >
      <tooltip
        bg-color="white"
        color="pink"
      >
        I'm so badass
      </tooltip>
    </q-btn>

    <q-btn
      label="Red & Yellow"
      no-caps
      color="primary"
      class="q-ma-lg"
    >
      <tooltip
        bg-color="red"
        color="yellow"
      >
        I'm so badass
      </tooltip>
    </q-btn>

    <q-btn
      label="Purple & White"
      no-caps
      color="primary"
      class="q-ma-lg"
    >
      <tooltip
        bg-color="purple"
        color="white"
      >
        I'm so badass
      </tooltip>
    </q-btn>

    <q-btn
      label="Primary"
      no-caps
      color="primary"
      class="q-ma-lg"
    >
      <tooltip
        bg-color="primary"
        color="white"
      >
        I'm so badass
      </tooltip>
    </q-btn>

    <q-btn
      label="Secondary"
      no-caps
      color="primary"
      class="q-ma-lg"
    >
      <tooltip
        bg-color="secondary"
        color="white"
      >
        I'm so badass
      </tooltip>
    </q-btn>

    <q-btn
      label="Positive"
      no-caps
      color="primary"
      class="q-ma-lg"
    >
      <tooltip
        bg-color="positive"
        color="white"
      >
        I'm so badass
      </tooltip>
    </q-btn>

    <q-btn
      label="Negative"
      no-caps
      color="primary"
      class="q-ma-lg"
    >
      <tooltip
        bg-color="negative"
        color="white"
      >
        I'm so badass
      </tooltip>
    </q-btn>

  </q-page>
</template>

<script>
  import {defineComponent, ref} from 'vue';

  export default defineComponent({
    name: 'PageIndex',
    components: {
      'tooltip': require('components/Tooltip').default
    },
    setup() {
      let showTooltip = ref(false)
      let showTooltipWithHide = ref(false)
      let showTooltipWithClose = ref(false)

      return {
        showTooltip,
        showTooltipWithHide,
        showTooltipWithClose
      }
    }
  })
</script>
