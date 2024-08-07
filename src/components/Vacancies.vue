<template>
  <div class="flex flex-col items-center justify-center gap-y-10 pt-10">
    <div>
      <label for="currency" class="p-4">Выберите валюту:</label>
      <select v-model="selectedCurrency">
        <option
          v-for="currency in currencies"
          :key="currency.label"
          :value="currency.label"
        >
          {{ currency.label }}
        </option>
      </select>
    </div>

    <div>
      <label for="titleFilter" class="p-4">Фильтр по названию:</label>
      <input v-model="titleFilter" />
    </div>

    <div>
      <label for="minSalary" class="p-4">Минимальная зарплата:</label>
      <input type="number" v-model.number="minSalary" />
      <label for="maxSalary" class="p-4">Максимальная зарплата:</label>
      <input type="number" v-model.number="maxSalary" />
    </div>

    <div>
      <label for="sortOrder" class="p-4">Сортировка:</label>
      <select v-model="sortOrder">
        <option value="asc">По возрастанию</option>
        <option value="desc">По убыванию</option>
      </select>
    </div>

    <ul class="flex flex-col gap-y-10 border-2 p-5">
      <li v-for="vacancy in sortedVacancies" :key="vacancy.id">
        <div v-if="!hiddenVacancies.has(vacancy.id)">
          <h3>{{ vacancy.title }}</h3>
          <p>Зарплата: {{ formatSalary(vacancy) }}</p>
          <button @click="hideVacancy(vacancy.id)">Скрыть</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, computed, watch } from "vue";
import VacanciesData from "./VacanciesData.vue";

type Currency = {
  label: string;
  coefficient: number;
};

type Salary = {
  value: number;
  currencies: Currency[];
};

type Vacancy = {
  id: number;
  title: string;
  salary: Salary;
};

export default defineComponent({
  name: "Vacancies",
  components: {
    VacanciesData,
  },
  setup() {
    //Json Data
    const vacancies = VacanciesData.data().vacancies;
    //Main Data
    const currencies = [
      { label: "USD", coefficient: 1.5 },
      { label: "RUB", coefficient: 1 },
    ];

    const selectedCurrency = ref("USD");
    const titleFilter = ref("");
    const minSalary = ref(0);
    const maxSalary = ref(Infinity);
    const sortOrder = ref("asc");
    const hiddenVacancies = ref<Set<number>>(new Set());

    watch(maxSalary, (newVal) => {
      if (newVal === "") {
        maxSalary.value = Infinity;
      }
    });

    // Functions

    function formatSalary(vacancy: Vacancy): string {
      const salaryInSelectedCurrency =
        vacancy.salary.value *
        (vacancy.salary.currencies.find(
          (c) => c.label === selectedCurrency.value
        )?.coefficient || 1);
      return `${salaryInSelectedCurrency} ${selectedCurrency.value}`;
    }

    function hideVacancy(id: number): void {
      hiddenVacancies.value.add(id);
    }

    //Main methods for filtering and sorting

    const filterVacancies = computed(() => {
      return vacancies.filter((vacancy) => {
        const salaryInSelectedCurrency =
          vacancy.salary.value *
          (vacancy.salary.currencies.find(
            (c) => c.label === selectedCurrency.value
          )?.coefficient || 1);

        return (
          !hiddenVacancies.value.has(vacancy.id) &&
          vacancy.title
            .toLowerCase()
            .includes(titleFilter.value.toLowerCase()) &&
          salaryInSelectedCurrency >= minSalary.value &&
          salaryInSelectedCurrency <= maxSalary.value
        );
      });
    });

    const sortedVacancies = computed(() => {
      return filterVacancies.value.sort((a, b) => {
        const salaryA =
          a.salary.value *
          (a.salary.currencies.find((c) => c.label === selectedCurrency.value)
            ?.coefficient || 1);
        const salaryB =
          b.salary.value *
          (b.salary.currencies.find((c) => c.label === selectedCurrency.value)
            ?.coefficient || 1);

        return sortOrder.value === "asc"
          ? salaryA - salaryB
          : salaryB - salaryA;
      });
    });

    return {
      selectedCurrency,
      titleFilter,
      minSalary,
      maxSalary,
      sortOrder,
      hiddenVacancies,
      sortedVacancies,
      currencies,
      formatSalary,
      hideVacancy,
    };
  },
});
</script>

<style scoped></style>
