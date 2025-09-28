<script setup lang="ts">
import type { CSSProperties } from 'vue'
import { computed } from 'vue'

const props = defineProps({
  background: {
    // random image from a curated Unsplash collection by Anthony
    default: 'https://source.unsplash.com/collection/94734566/1920x1080',
  },
})

function resolveAssetUrl(url: string) {
  if (url.startsWith('/'))
    return import.meta.env.BASE_URL + url.slice(1)
  return url
}

function handleBackground(background?: string, dim = false): CSSProperties {
  const isColor = background && ['#', 'rgb', 'hsl'].some(v => background.indexOf(v) === 0)

  const style = {
    background: isColor
      ? background
      : undefined,
    color: (background && !isColor)
      ? 'white'
      : undefined,
    backgroundImage: isColor
      ? undefined
      : background
        ? dim
          ? `linear-gradient(#0005, #0008), url(${CSS.escape(resolveAssetUrl(background))})`
          : `url("${CSS.escape(resolveAssetUrl(background))}")`
        : undefined,
    backgroundRepeat: 'no-repeat',
    backgroundPosition: 'center',
    backgroundSize: 'cover',
  }

  if (!style.background)
    delete style.background

  return style
}

const style = computed(() => handleBackground(props.background, true))
</script>

<template>
  <div class="slidev-layout title-blob" :style="style">
    <div class="blob-wrapper">
      <div class="blob-shape"></div>
      <div class="blob-content">
        <slot />
      </div>
    </div>
  </div>
</template>

<style scoped>
.title-blob {
  position: relative;
  width: 100%;
  height: 100%;
  overflow: hidden;
}

/* wrapper placed bottom-right, small size */
.blob-wrapper {
  position: absolute;
  bottom: 2rem;
  right: 2rem;
  width: 35%; /* make it smaller */
  max-width: 400px;  /* cap its size */
  aspect-ratio: 1 / 1;
  pointer-events: none;
}

/* blob shape with border and organic rounding */
.blob-shape {
  position: absolute;
  inset: 0;
  /* organic “blob-like” border-radius using 8-value trick */  
  border-radius: 55% 45% 60% 50% / 50% 60% 45% 55%;
  background: rgba(255, 255, 255, 0.9);
  border: 3px solid rgba(0, 0, 0, 0.8);
}

/* content centered inside */
.blob-content {
  position: absolute;
  inset: 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: 1.5rem;
  z-index: 2;
  pointer-events: none;
  color: #111; /* change depending on your background */
}

/* Responsive tweak */
@media (max-width: 768px) {
  .blob-wrapper {
    width: 50%;
    bottom: 1rem;
    right: 1rem;
  }
  .blob-content {
    padding: 1rem;
  }
}
</style>

