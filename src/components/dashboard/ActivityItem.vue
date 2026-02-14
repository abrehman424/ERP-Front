<template>
  <div 
    :class="cardClasses"
    v-bind="accessibilityAttrs"
    @click="handleClick"
    @keydown="handleKeydown"
    tabindex="0"
    role="button"
  >
    <!-- Glow layer -->
    <div
      v-if="enableGlow"
      class="absolute inset-0 opacity-0 group-hover:opacity-60 transition-opacity duration-400 pointer-events-none"
      :style="glowStyles"
    />

    <div class="flex items-center  gap-3.5 relative py-2 ">
      <!-- Colored icon circle -->
      <div
        class="sm:w-11 sm:h-11   flex items-center justify-center flex-shrink-0 transform group-hover:scale-110 group-hover:rotate-3 transition-all duration-300"
      >
        <div class="" v-html="activity.svg"></div>
      </div>

      <!-- Main content -->
      <div class="flex-1 min-w-0 gap-2">
        <div class="flex items-baseline  gap-2">
          <p class="text-sm sm:text-base font-bold text-[#0F172A] ">
            {{ activity.content }}
          </p>

          <!-- Status badge (Pending, etc.) -->
          <span
            v-if="activity.badge"
            :class="[
              'inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-medium whitespace-nowrap',
              badgeClasses
            ]"
          >
            {{ activity.badge }}
          </span>
        </div>

        <!-- Time -->
        

        <!-- Details line + small SVG at the end -->
        <div class=" flex items-center justify-between text-sm font-normal text-[#64748B]">
          <span>{{ activity.details }}</span>
        </div>

        <p class=" text-[10px] text-[#94A3B8] flex items-center gap-1.5">
         
          {{ activity.time }}
        </p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue'
import { Clock } from 'lucide-vue-next'
import { useInteractiveCard } from '@/composables/useInteractiveCard' // assuming you still use this

const props = defineProps({
  activity: { type: Object, required: true },
  size: { type: String, default: 'md' },
  variant: { type: String, default: 'minimal' },
  enableGlow: { type: Boolean, default: true },
  glowColor: { type: String, default: null }
})

const emit = defineEmits(['click'])

const {
  Classes: baseClasses,
  glowStyles: baseGlowStyles,
  handleClick,
  handleKeydown,
  accessibilityAttrs
} = useInteractiveCard(props, emit)

const Classes = computed(() => [
  baseClasses.value,
  'border border-gray-200/50 bg-white/80 backdrop-blur-sm',
  'hover:bg-white/90 hover:shadow-md transition-all duration-300',
  'group cursor-pointer'
].join(' '))

const glowStyles = computed(() => {
  const color = props.glowColor || props.activity.color || '#6366F1'
  return {
    background: `radial-gradient(circle at 20% 50%, ${color}18 0%, transparent 65%)`
  }
})

const badgeClasses = computed(() => {
  const typeMap = {
    success: 'bg-[#F1F5F9] text-[#64748B]',
    primary: 'bg-[#FEF3C7] text-[#B45309]'
  }

  return typeMap[props.activity.type] || 'bg-gray-100 text-gray-800'
})

</script>