<template>
  <div class="relative flex flex-col w-full h-24 items-center justify-center">
    <button
      @click="handleClick"
      class="bg-foreground text-background px-4 py-2 rounded-lg hover:scale-110 transition duration-500"
    >
      Trigger Side Cannons
    </button>
  </div>
</template>

<script setup lang="ts">
import confetti from "canvas-confetti";

// Function to trigger the confetti side cannons
const handleClick = () => {
  const end = Date.now() + 3 * 1000; // 3 seconds
  const colors = ["#a786ff", "#fd8bbc", "#eca184", "#f8deb1"];

  // Frame function to trigger confetti cannons
  const frame = () => {
    if (Date.now() > end) return;

    // Left side confetti cannon
    confetti({
      particleCount: 2,
      angle: 60,
      spread: 55,
      startVelocity: 60,
      origin: { x: 0, y: 0.5 },
      colors: colors,
    });

    // Right side confetti cannon
    confetti({
      particleCount: 2,
      angle: 120,
      spread: 55,
      startVelocity: 60,
      origin: { x: 1, y: 0.5 },
      colors: colors,
    });

    requestAnimationFrame(frame); // Keep calling the frame function
  };

  frame();
};
</script>
