<template>
  <section class="flex items-center justify-between">
    <div>
      <label
        for="search-country"
        class="flex h-14 w-120 items-center gap-6 rounded bg-brand-white-1 px-8 text-brand-gray-1 shadow-dark-2 transition ease-in dark:bg-brand-dark-1 dark:text-brand-white-1"
      >
        <font-awesome-icon :icon="['fas', 'magnifying-glass']" />
        <input
          id="search-country"
          type="text"
          class="h-full w-full bg-transparent outline-none transition ease-in"
          placeholder="Search for a country..."
        />
      </label>
    </div>

    <div class="relative">
      <div
        class="relative flex h-14 w-60 cursor-pointer items-center justify-between gap-14 rounded bg-brand-white-1 px-6 text-brand-gray-1 shadow-dark-2 transition dark:bg-brand-dark-1 dark:text-brand-white-1"
        @click="handleFilterRegions"
      >
        <span v-if="selectedRegion">{{ selectedRegion }}</span>
        <span v-else>Filter by region</span>
        <font-awesome-icon :icon="['fas', 'angle-down']" class="" />
      </div>

      <ul
        v-if="filterRegionsVisibility"
        class="absolute left-0 top-16 flex w-full flex-col rounded bg-brand-white-1 text-brand-gray-1 shadow-dark-2 dark:bg-brand-dark-1 dark:text-brand-white-1"
      >
        <template v-for="region in regions">
          <li
            v-if="region !== selectedRegion"
            :key="region"
            class="cursor-pointer px-6 py-3 hover:bg-brand-gray-2 dark:hover:bg-brand-dark-3"
            @click="chooseRegion"
          >
            {{ region }}
          </li>
        </template>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  name: "InputFilter",
  data() {
    return {
      filterRegionsVisibility: true,
      regions: ["All", "Africa", "America", "Asia", "Europe", "Oceania"],
      selectedRegion: "",
    };
  },
  methods: {
    handleFilterRegions() {
      this.filterRegionsVisibility = !this.filterRegionsVisibility;
    },
    chooseRegion($event) {
      this.selectedRegion = $event.target.textContent;
      this.filterRegionsVisibility = !this.filterRegionsVisibility;
    },
  },
};
</script>
