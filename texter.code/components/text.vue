<script lang="ts" setup>
const props = defineProps({
  text: {
    type: Object as PropType<{ content: string; author: string; date: string }>,
    required: true,
  },
  active: { type: Boolean, default: false },
});

const { $dayjs } = useNuxtApp();
const date = computed(() => {
  const date = $dayjs(props.text.date);

  if (Math.abs($dayjs().diff(date, "days")) > 2) {
    return date.format("DD MMMM YYYY HH:mm");
  }

  return date.fromNow();
});
</script>

<template>
  <div class="text-frame" :class="{ active }">
    <div class="px-5 mt-5" style="line-height: 1.1">
      <div>{{ text.author }}</div>
      <div style="font-size: 70%">
        {{ date }}
      </div>
    </div>
    <div class="pa-5">
      <!-- {{ text.content }} -->
      <MDC :value="text.content" />
    </div>
  </div>
</template>

<style lang="scss">
.text-frame {
  border-radius: 0.6em;
  border: 1px solid rgba(var(--v-theme-on-background), 0.05);
  transition: all 0.5s ease;

  &.active {
    // border-width: 3px;
    box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
  }
}
</style>
