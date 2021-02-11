<template>
  <!--
  Tailwind UI components require Tailwind CSS v1.8 and the @tailwindcss/ui plugin.
  Read the documentation to get started: https://tailwindui.com/documentation
-->
  <nav class="bg-brand-primary fixed w-full z-10">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 top-0">
      <div class="flex items-center justify-between h-24">
        <div class="flex-shrink-0">
          <a href="/">
            <img
              class="block h-16 w-auto"
              src="~/assets/logos/DevEdmonton-Logo-Light.svg"
              alt="Workflow logo"
            />
          </a>
        </div>
        <div class="hidden sm:block sm:ml-6">
          <div class="flex">
            <a
              v-for="link in menuLinks"
              :key="link.name"
              :href="link.href"
              class="ml-4 px-3 py-2 rounded-md text-sm font-medium leading-5 text-white hover:bg-brand-primary-dark focus:outline-none focus:text-white focus:bg-brand-primary-dark transition duration-150 ease-in-out"
            >
              {{ link.name }}
            </a>
          </div>
        </div>

        <div class="-mr-2 flex sm:hidden">
          <!-- Mobile menu button -->
          <button
            id="mobile-btn"
            @click="toggleMenu"
            class="inline-flex items-center justify-center p-2 rounded-md text-white hover:bg-brand-primary-dark focus:outline-none focus:bg-brand-primary-dark transition duration-150 ease-in-out"
            aria-label="Main menu"
            aria-expanded="false"
          >
            <!-- Icon when menu is closed. -->
            <!--
            Heroicon name: menu

            Menu open: "hidden", Menu closed: "block"
          -->
            <svg
              class="block h-6 w-6"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M4 6h16M4 12h16M4 18h16"
              />
            </svg>
            <!-- Icon when menu is open. -->
            <!--
            Heroicon name: x

            Menu open: "block", Menu closed: "hidden"
          -->
            <svg
              class="hidden h-6 w-6"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M6 18L18 6M6 6l12 12"
              />
            </svg>
          </button>
        </div>
      </div>
    </div>

    <!--
    Mobile menu, toggle classes based on menu state.

    Menu open: "block", Menu closed: "hidden"
  -->
    <div id="mobile-menu" class="hidden sm:hidden">
      <div class="px-2 pt-2 pb-3">
        <a
          v-for="link in menuLinks"
          :key="link.name"
          @click="toggleMenu"
          :href="link.href"
          class="mt-1 block px-3 py-2 rounded-md text-base font-medium text-white hover:text-white hover:bg-brand-primary-dark focus:outline-none focus:text-white focus:bg-brand-primary-dark transition duration-150 ease-in-out"
        >
          {{ link.name }}
        </a>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  methods: {
    toggleMenu: function () {
      const mobileMenu = document.getElementById("mobile-menu");
      mobileMenu.classList.toggle("hidden");
      mobileMenu.classList.toggle("block");
    },
  },
  data: function () {
    return {
      menuLinks: [
        {
          name: "What We Do",
          href: "/#what-we-do",
        },
        {
          name: "Get Involved",
          href: "/#get-involved",
        },
        {
          name: "Board",
          href: "/board",
        },
        {
          name: "Become a Member test",
          href: "/become_a_member",
        },
        {
          name: "Code of Conduct",
          href: "/code_of_conduct/"
        },
        {
          name: "Contact",
          href: "/contact",
        },
      ],
    };
  },
  computed: {},
};
</script>
