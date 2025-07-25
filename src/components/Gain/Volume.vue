<template>
  <div class="p-4 flex justify-center">
    <input
      type="number"
      class="font-arial text-2xl font-bold text-slate-800 bg-transparent border-b border-gray-300 w-20 text-center focus:outline-none focus:ring-1 focus:ring-blue-400"
      :value="(gain * 100).toFixed(1)"
      step="0.5"
      min="0"
      :max="settings.max"
      @input="(e) =>
        setGain(
          clamp(parseFloat((e.target as HTMLInputElement).value) / 100, 0, settings.max / 100)
        )"
    />
    <span class="ml-1 text-2xl font-bold text-slate-800">%</span>
  </div>
</template>

<script setup lang="ts">
import { clamp } from 'lodash'

import useGain from '@/composables/useGain.ts'
import useSettings from '@/composables/useSettings.ts'
import { setGain } from '@/store/gain.ts'

const { gain } = useGain()
const { settings } = useSettings()
</script>
