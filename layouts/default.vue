<script setup>
import { ref, onMounted } from "vue";

// Reactive state for screen size
const isDesktop = ref(false);
const isSidebarOpen = ref(false);

// Check screen size on mount and when window is resized
onMounted(() => {
  checkScreenSize();
  window.addEventListener("resize", checkScreenSize);
});

function checkScreenSize() {
  isDesktop.value = window.innerWidth >= 1024; // 1024px is standard lg breakpoint in Tailwind
}

function toggleSidebar() {
  isSidebarOpen.value = !isSidebarOpen.value;
}
</script>

<template>
  <div class="flex flex-col min-h-screen bg-background">
    <!-- Mobile Header (shown only on mobile) -->
    <header v-if="!isDesktop" class="bg-secondary/80 backdrop-blur-md sticky top-0 left-0 right-0 z-10">
      <div
        class="container sticky mx-auto px-4 py-3 flex gap-2 justify-between items-center"
      >
        <div class="logo">
          <h1 class="text-md font-semibold">
            Markdown Blog
          </h1>
        </div>
      </div>
    </header>

    <!-- Desktop Navigation (shown only on desktop) -->
    <nav v-if="isDesktop" class="shadow-md">
      <div class="container mx-auto px-4 py-3">
        <div class="flex justify-between items-center">
          <div class="logo">
            <NuxtLink to="/" class="text-xl font-bold">Markdown Blog</NuxtLink>
          </div>
          
        </div>
      </div>
    </nav>

    <!-- Main Content -->
    <main class="flex-grow pt-5 lg:pt-0">
      <!-- This is where your page content will be injected -->
      <slot />
    </main>

    <!-- Footer -->
    <footer class="border-t">
      <div class="container mx-auto px-4 py-4 text-center text-gray-600">
        &copy; {{ new Date().getFullYear() }} markdown-blog-nuxt
      </div>
    </footer>
  </div>
</template>
