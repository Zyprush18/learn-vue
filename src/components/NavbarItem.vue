<script setup>
import { ref,reactive,onMounted } from "vue";
defineProps({
  msg: {
    type: String,
    required: true,
  },
});

const itemnav = reactive([
  {
    Menu: "Home",
    Src: "#home",
  },
  {
    Menu: "About",
    Src: "#about",
  },
  {
    Menu: "Project Me",
    Src: "#projectme",
  },
  {
    Menu: "Contact Me",
    Src: "#conteactme",
  },
]);

const isDark = ref(false);

onMounted(() => {
  // Cek preferensi awal
  if (
    localStorage.theme === "dark" ||
    (!("theme" in localStorage) && window.matchMedia("(prefers-color-scheme: dark)").matches)
  ) {
    isDark.value = true;
  }
  applyTheme();
});

function applyTheme() {
  document.documentElement.classList.toggle("dark", isDark.value);
  localStorage.theme = isDark.value ? "dark" : "light";
}


</script>

<template>
  <div class="drawer">
    <input id="my-drawer-3" type="checkbox" class="drawer-toggle" />
    <div class="drawer-content flex flex-col">
      <!-- Navbar -->
      <div class="navbar w-full px-5 bg-white shadow-sm dark:bg-black">
        <div class="navbar-start">
          <div class="flex-none text-black lg:hidden">
            <label for="my-drawer-3" aria-label="open sidebar" class="btn btn-square btn-ghost">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                class="inline-block h-6 w-6 stroke-current"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M4 6h16M4 12h16M4 18h16"
                ></path>
              </svg>
            </label>
          </div>
          <h1 class="text-3xl font-bold mx-2 flex-1 px-2 text-black dark:text-white">{{ msg }}</h1>
        </div>
        <div class="navbar-center hidden flex-none lg:block">
          <ul class="menu menu-horizontal px-1">
            <!-- Navbar menu content here -->
            <li :key="i" v-for="i in itemnav" class="text-lg text-black dark:text-white">
              <a :href="i.Src">{{ i.Menu }}</a>
            </li>
          </ul>
        </div>
        <div class="navbar-end">
          <!-- theme controller -->
          <label class="swap swap-rotate  text-black dark:text-white">
            <!-- this hidden checkbox controls the state -->
            <input type="checkbox" class="theme-controller" value="synthwave" @click="applyTheme"/>

            <!-- sun icon -->
            <svg
              class="swap-off h-10 w-10 fill-current"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
            >
              <path
                d="M5.64,17l-.71.71a1,1,0,0,0,0,1.41,1,1,0,0,0,1.41,0l.71-.71A1,1,0,0,0,5.64,17ZM5,12a1,1,0,0,0-1-1H3a1,1,0,0,0,0,2H4A1,1,0,0,0,5,12Zm7-7a1,1,0,0,0,1-1V3a1,1,0,0,0-2,0V4A1,1,0,0,0,12,5ZM5.64,7.05a1,1,0,0,0,.7.29,1,1,0,0,0,.71-.29,1,1,0,0,0,0-1.41l-.71-.71A1,1,0,0,0,4.93,6.34Zm12,.29a1,1,0,0,0,.7-.29l.71-.71a1,1,0,1,0-1.41-1.41L17,5.64a1,1,0,0,0,0,1.41A1,1,0,0,0,17.66,7.34ZM21,11H20a1,1,0,0,0,0,2h1a1,1,0,0,0,0-2Zm-9,8a1,1,0,0,0-1,1v1a1,1,0,0,0,2,0V20A1,1,0,0,0,12,19ZM18.36,17A1,1,0,0,0,17,18.36l.71.71a1,1,0,0,0,1.41,0,1,1,0,0,0,0-1.41ZM12,6.5A5.5,5.5,0,1,0,17.5,12,5.51,5.51,0,0,0,12,6.5Zm0,9A3.5,3.5,0,1,1,15.5,12,3.5,3.5,0,0,1,12,15.5Z"
              />
            </svg>

            <!-- moon icon -->
            <svg
              class="swap-on h-10 w-10 fill-current"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
            >
              <path
                d="M21.64,13a1,1,0,0,0-1.05-.14,8.05,8.05,0,0,1-3.37.73A8.15,8.15,0,0,1,9.08,5.49a8.59,8.59,0,0,1,.25-2A1,1,0,0,0,8,2.36,10.14,10.14,0,1,0,22,14.05,1,1,0,0,0,21.64,13Zm-9.5,6.69A8.14,8.14,0,0,1,7.08,5.22v.27A10.15,10.15,0,0,0,17.22,15.63a9.79,9.79,0,0,0,2.1-.22A8.11,8.11,0,0,1,12.14,19.73Z"
              />
            </svg>
          </label>
        </div>
      </div>
    </div>

    <div class="drawer-side">
      <label for="my-drawer-3" aria-label="close sidebar" class="drawer-overlay"></label>
      <ul class="menu bg-white dark:bg-base-200 min-h-full w-80 p-8">
        <!-- Sidebar content here -->
        <li :key="i" v-for="i in itemnav" class="m-6 text-black dark:text-white">
          <a :href="i.Src">{{ i.Menu }}</a>
        </li>
      </ul>
    </div>
  </div>
</template>
