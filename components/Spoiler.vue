<template>
  <div class="spoilers-block">
    <div
      v-for="(item, i) in items"
      :key="i"
      class="spoiler"
      @click="showFAQ(i)"
    >
      <div class="spoiler-title" :class="{ opened: item.show }">
        {{ item.title }}
      </div>
      <transition name="fade">
        <div v-if="item.show" class="spoiler-answer">
          {{ item.text }}
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Spoiler',
  props: {
    items: {
      type: Array,
      default: () => {},
    },
  },
  data() {
    return {
      spoilers: this.items,
    }
  },
  methods: {
    showFAQ(i) {
      if (this.spoilers[i].show) {
        this.spoilers[i].show = false
      } else {
        for (let j = 0; j < this.spoilers.length; j++) {
          this.spoilers[j].show = false
        }
        this.spoilers[i].show = true
      }
    },
  },
}
</script>

<style scoped>
.spoilers-block {
  display: flex;
  flex-direction: column;
  margin: 50px 0;
}

.spoiler {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  padding: 20px;
  border: 1px solid;
  border-bottom: none;
}

.spoiler:last-child {
  border-bottom: 1px solid;
}

.spoiler-title {
  font-size: 20px;
}
.opened {
  margin-bottom: 15px;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s, height 0.2s, transform 0.2s, padding 200ms;
  will-change: opacity, height, transform, padding;
}

.fade-enter,
.fade-leave-to {
  transform: scale(0.8);
  opacity: 0;
  height: 0;
  padding: 0;
}
</style>
