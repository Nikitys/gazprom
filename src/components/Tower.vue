<template lang="pug">
  .tower 
    .top
      .title(
        v-text="tower.title"
      )
      .value(
        v-text="valueInPercent  + '%'"
      )
      .line(
        :class="[colorLineClass]"
      )
    .main
      svg(width="155px" height="497px" viewBox="0 0 155 497" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink")
          <defs>
              <linearGradient x1="2.45287691%" y1="50.0068553%" x2="100.021923%" y2="49.9967356%" id="linearGradient-1">
                  <stop stop-color="#616166" offset="0%"></stop>
                  <stop stop-color="#9B9B9B" offset="21%"></stop>
                  <stop stop-color="#48484F" offset="100%"></stop>
              </linearGradient>
              <linearGradient x1="2.45287691%" y1="49.9458107%" x2="100.021923%" y2="49.9458107%" id="linearGradient-2">
                  <stop stop-color="#616166" offset="0%"></stop>
                  <stop stop-color="#9B9B9B" offset="21%"></stop>
                  <stop stop-color="#48484F" offset="100%"></stop>
              </linearGradient>
              <linearGradient x1="2.45287691%" y1="49.9985854%" x2="100.021923%" y2="49.9985854%" id="linearGradient-3">
                  <stop stop-color="#616166" offset="0%"></stop>
                  <stop stop-color="#9B9B9B" offset="21%"></stop>
                  <stop stop-color="#48484F" offset="100%"></stop>
              </linearGradient>
              <linearGradient x1="2.45287691%" y1="49.9425462%" x2="100.021923%" y2="49.9425462%" id="linearGradient-4">
                  <stop stop-color="#616166" offset="0%"></stop>
                  <stop stop-color="#9B9B9B" offset="21%"></stop>
                  <stop stop-color="#48484F" offset="100%"></stop>
              </linearGradient>
              <linearGradient x1="0.0170429716%" y1="50.0049608%" x2="100.023598%" y2="50.0049608%" id="linearGradient-5">
                  <stop stop-color="#616166" offset="0%"></stop>
                  <stop stop-color="#9B9B9B" offset="21%"></stop>
                  <stop stop-color="#48484F" offset="100%"></stop>
              </linearGradient>
          </defs>
          g#Page-1(stroke='none' stroke-width='1' fill='none' fill-rule='evenodd')
            g#tower(transform='translate(0.000000, 2.000000)')
              g#Group(transform='translate(0.000000, 0.000000)')
                rect#Rectangle-path(fill='#CBCBCB' fill-rule='nonzero' x='0' y='4.9' width='154.6' height='4.3')
                rect#Rectangle-path(fill='url(#linearGradient-1)' fill-rule='nonzero' x='8.6' y='12' width='137.3' height='91.9')
                rect#Rectangle-path(fill='#CBCBCB' fill-rule='nonzero' x='0' y='410.7' width='154.6' height='4.3')
                rect#Rectangle-path(fill='url(#linearGradient-2)' fill-rule='nonzero' x='8.6' y='113.5' width='137.3' height='91.9')
                rect#Rectangle-path(fill='url(#linearGradient-3)' fill-rule='nonzero' x='8.6' y='214.9' width='137.3' height='91.9')
                rect#Rectangle-path(fill='url(#linearGradient-4)' fill-rule='nonzero' x='8.6' y='316.4' width='137.3' height='91.9')
                polygon#Shape(fill='url(#linearGradient-5)' fill-rule='nonzero' points='68.6 494.4 8.6 417.8 145.9 417.8 86 494.4')
                rect#Rectangle-path(fill='#21B249' fill-rule='nonzero' opacity='0.5' x='18.9' :y='yTower' width='118.5' :height='heightTower')
                rect#Rectangle-path(fill='#CBCBCB' fill-rule='nonzero' x='0' y='207.8' width='154.6' height='4.3')
                rect#Rectangle-path(fill='#CBCBCB' fill-rule='nonzero' x='0' y='309.2' width='154.6' height='4.3')
                rect#Rectangle-path(fill='#CBCBCB' fill-rule='nonzero' x='0' y='106.3' width='154.6' height='4.3')
                path#Shape(d='M53.7,0.6 L100.9,0.6' stroke='#8B959F' stroke-width='4')
                path#Shape(d='M75.9,477.1 L25.4,477.1 C19.9,477.1 15.4,472.6 15.4,467.1 L15.4,443.2 C15.4,437.7 19.9,433.2 25.4,433.2 L75.9,433.2 C81.4,433.2 85.9,437.7 85.9,443.2 L85.9,467.1 C85.9,472.6 81.4,477.1 75.9,477.1 Z' stroke='#21B149' stroke-width='3')

      </svg>
    .bottom
      .title Масса карналита
      .value(
        v-text="tower.value"
      )

</template>

<script>
export default {
  props: {
    tower: Object
  },

  data() {
    return {
      maxHeight: 400
    }
  },

  computed: {
    valueInPercent() {
      const maxValue = this.tower.maxValue;
      const value = this.tower.value;
      return Math.round(value / (maxValue / 100));
    },

    heightTower() {
      const heightTower = this.valueInPercent * (this.maxHeight / 100);
      if (heightTower > this.maxHeight) {
        return this.maxHeight
      } else {
        return  heightTower
      }
    },

    yTower() {
      return this.maxHeight - this.heightTower + 6
    },

    colorLineClass() {
      if (
        this.tower.value > this.tower.minValue &&
        this.tower.value < this.tower.maxValue
      ) {
        return "-green";
      }
      return "-red";
    }
  }
};
</script>

<style scoped lang="scss">
.tower {
  & > .top {
    text-align: center;
    color: #fff;
    & > .title {
      font-size: 1.5rem;
      max-width: 155px;
      margin-bottom: 1rem;
    }
    & > .value {
      font-size: 2rem;
    }
    .line {
      width: 3rem;
      height: 0.2rem;
      margin: 0.2rem auto 1rem;
      &.-red {
        background: red;
      }
      &.-green {
        background: green;
      }
    }
  }
  & > .bottom {
    text-align: center;
    color: #fff;
    font-size: 1.2rem;
    margin-top: 1rem;
    & > .value {
      font-size: 2rem;
      border-bottom: 3px solid green;
      display: inline-block;
    }
  }
}
</style>
