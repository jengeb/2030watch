<template>
  <svg class="sdg-vis">
    <line
      class="range"
      stroke-linecap="round"
      x1="0%"
      y1="50%"
      x2="100%"
      y2="50%" />
    <line
      class="diff"
      :stroke="color"
      :x1="sdg.total + '%'"
      y1="50%"
      :x2="sdg.dns + '%'"
      y2="50%" />
    <circle
      class="sdg-marker sdg-marker-total"
      :cx="sdg.total + '%'"
      cy="50%"
      r="8" />
    <text
      class="sdg-label sdg-label-total"
      alignment-baseline="baseline"
      :text-anchor="sdg.total > 50 ? 'end' : 'start'"
      :x="sdg.total + (sdg.total > 50 ? -3 : 3) + '%'"
      y="40%">
      {{ sdg.total }}%
    </text>
    <circle
      class="sdg-marker sdg-marker-dns"
      :cx="sdg.dns + '%'"
      cy="50%"
      r="8" />
    <text
      class="sdg-label sdg-label-dns"
      alignment-baseline="hanging"
      :text-anchor="sdg.dns > 50 ? 'end' : 'start'"
      :x="sdg.dns + (sdg.dns > 50 ? -3 : 3) + '%'"
      y="60%">
      {{ sdg.dns }}%
    </text>
  </svg>
</template>

<script>
  // import chroma from 'chroma-js'

  // const diffScale = chroma.scale(['#D22F27', '#eee', '#5C9E31']).domain([-100, 0, 100])

  export default {
    props: ['sdg'],
    computed: {
      color (state) {
        console.log(this, state)
        // return diffScale(this.dns - this.okf).hex()
      }
    }
  }
</script>

<style lang="scss" scoped>
  .sdg-vis {
    flex: 1;
    height: 100%;

    .range {
      stroke: #ebecf1;
      stroke-width: 4px;
    }

    .diff {
      stroke-width: 4px;
    }

    .sdg-marker {
      stroke: #f9f9f9;
      stroke-width: 2px;

      &.sdg-marker-total {
        fill: #04A6F0;
      }

      &.sdg-marker-dns {
        fill: #F1B31C;
      }
    }

    .sdg-label {
      opacity: 0;
      font-size: 12px;

      &.sdg-label-total {
        fill: #04A6F0;
      }

      &.sdg-marker-dns {
        fill: #F1B31C;
      }
    }
  }
</style>
