<template>
  <div>
    <div class="top-row">
      <div class="top part">
        <div class="robot-name">
          {{selectedRobot.head.title}}
        </div>
        <span v-if="selectedRobot.head.onSale" class="sale">Sale!</span>
        <img :src="selectedRobot.head.src"
          title="head"
        />
        <button @click="prevHead()" class="prev-selector">&#9668;</button>
        <button @click="nextHead()" class="next-selector">&#9658;</button>
      </div>
    </div>
    <div class="middle-row">
      <div class="left part">
        <img :src="selectedRobot.leftArm.src" title="left arm" />
        <button @click="prevLArm()" class="prev-selector">&#9650;</button>
        <button @click="nextLArm()" class="next-selector">&#9660;</button>
      </div>
      <div class="center part">
        <img :src="selectedRobot.torsos.src" title="left arm" />
        <button @click="prevTorsos()" class="prev-selector">&#9668;</button>
        <button @click="nextTorsos()" class="next-selector">&#9658;</button>
      </div>
      <div class="right part">
        <img :src="selectedRobot.rightArm.src" title="left arm" />
        <button @click="prevRArm()" class="prev-selector">&#9668;</button>
        <button @click="nextRArm()" class="next-selector">&#9658;</button>
      </div>
    </div>
    <div class="bottom-row">
      <div class="bottom part">
        <img :src="selectedRobot.bottom.src" title="left arm" />
        <button @click="prevBottom()" class="prev-selector">&#9668;</button>
        <button @click="nextBottom()" class="next-selector">&#9658;</button>
      </div>
    </div>
  </div>
</template>

<script>
import availableParts from '../data/parts'

function getPrevValidIdx (index, length) {
  const nextVal = index - 1
  return nextVal < 0 ? length - 1 : nextVal
}

function getNextValidIdx (index, length) {
  const nextVal = index + 1
  return nextVal > length - 1 ? 0 : nextVal
}
export default {
  name: 'RobotBuilder',
  data () {
    return {
      availableParts,
      selectedHeadIndex: 0,
      selectedLArmIndex: 0,
      selectedRArmIndex: 0,
      selectedTorsosIndex: 0,
      selectedBottomIndex: 0
    }
  },
  computed: {
    selectedRobot: function () {
      console.log(availableParts.heads[this.selectedHeadIndex].src)
      console.log(availableParts.arms[this.selectedLArmIndex].src)
      console.log(availableParts.torsos[this.selectedTorsosIndex].src)
      console.log(availableParts.arms[this.selectedRArmIndex].src)
      console.log(availableParts.bases[this.selectedBottomIndex].src)
      return {
        head: availableParts.heads[this.selectedHeadIndex],
        leftArm: availableParts.arms[this.selectedLArmIndex],
        torsos: availableParts.torsos[this.selectedTorsosIndex],
        rightArm: availableParts.arms[this.selectedRArmIndex],
        bottom: availableParts.bases[this.selectedBottomIndex]
      }
    }
  },
  methods: {
    nextHead () {
      this.selectedHeadIndex = getNextValidIdx(this.selectedHeadIndex, availableParts.heads.length)
    },
    prevHead () {
      this.selectedHeadIndex = getPrevValidIdx(this.selectedHeadIndex, availableParts.heads.length)
    },
    nextLArm () {
      this.selectedLArmIndex = getNextValidIdx(this.selectedLArmIndex, availableParts.arms.length)
    },
    prevLArm () {
      this.selectedLArmIndex = getPrevValidIdx(this.selectedLArmIndex, availableParts.arms.length)
    },
    nextRArm () {
      this.selectedRArmIndex = getNextValidIdx(this.selectedRArmIndex, availableParts.arms.length)
    },
    prevRArm () {
      this.selectedRArmIndex = getPrevValidIdx(this.selectedRArmIndex, availableParts.arms.length)
    },
    nextTorsos () {
      this.selectedTorsosIndex = getNextValidIdx(this.selectedTorsosIndex, availableParts.torsos.length)
    },
    prevTorsos () {
      this.selectedTorsosIndex = getPrevValidIdx(this.selectedTorsosIndex, availableParts.torsos.length)
    },
    nextBottom () {
      this.selectedBottomIndex = getNextValidIdx(this.selectedBottomIndex, availableParts.bases.length)
    },
    prevBottom () {
      this.selectedBottomIndex = getPrevValidIdx(this.selectedBottomIndex, availableParts.bases.length)
    }
  }
}
</script>

<style>
.part {
  position: relative;
  width: 165px;
  height: 165px;
  border: 3px solid #aaa;
}
.part img {
  width: 165px;
}
.top-row {
  display: flex;
  justify-content: space-around;
}
.middle-row {
  display: flex;
  justify-content: center;
}
.bottom-row {
  display: flex;
  justify-content: space-around;
  border-top: none;
}
.head {
  border-bottom: none;
}
.left {
  border-right: none;
}
.right {
  border-left: none;
}
.left img {
  transform: rotate(-90deg);
}
.right img {
  transform: rotate(90deg);
}
.bottom {
  border-top: none;
}
.prev-selector {
  position: absolute;
  z-index: 1;
  top: -3px;
  left: -28px;
  width: 25px;
  height: 171px;
}
.next-selector {
  position: absolute;
  z-index: 1;
  top: -3px;
  right: -28px;
  width: 25px;
  height: 171px;
}
.center .prev-selector,
.center .next-selector {
  opacity: 0.8;
}
.left .prev-selector {
  top: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.left .next-selector {
  top: auto;
  bottom: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.right .prev-selector {
  top: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  top: auto;
  bottom: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  right: -3px;
}
.robot-name {
  position: absolute;
  top: -25px;
  text-align: center;
  width: 100%;
}
.sale {
  color: red;
}
</style>
