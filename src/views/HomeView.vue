<script setup>
import TheWelcome from "../components/TheWelcome.vue";
import Children from "../components/Children.vue";
</script>

<template>
  <main>
    <TheWelcome />
    <Children />
  </main>
</template>

<script>
export default {
  mounted() {
    const observer = new IntersectionObserver((entries) => {
      entries.forEach((entry) => {
        console.log(entry);
        if (entry.isIntersecting) {
          entry.target.classList.add("show");
        } else {
          entry.target.classList.remove("show");
        }
      });
    });

    const hiddenElements = document.querySelectorAll(".hidden");
    hiddenElements.forEach((el) => observer.observe(el));
  },
};
</script>
