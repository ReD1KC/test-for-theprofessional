<template></template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "VacanciesData",
  data() {
    return {
      vacancies: [
        {
          id: 1,
          title: "Frontend Developer",
          salary: {
            value: 10000,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 2,
          title: "Backend Developer",
          salary: {
            value: 8000,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 3,
          title: "Full Stack Developer",
          salary: {
            value: 12000,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 4,
          title: "UI/UX Designer",
          salary: {
            value: 9500,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 5,
          title: "DevOps Engineer",
          salary: {
            value: 11000,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 6,
          title: "Product Manager",
          salary: {
            value: 13000,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 7,
          title: "QA Engineer",
          salary: {
            value: 9000,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 8,
          title: "Database Administrator",
          salary: {
            value: 10500,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 9,
          title: "Network Engineer",
          salary: {
            value: 8500,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 10,
          title: "Systems Analyst",
          salary: {
            value: 9800,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 11,
          title: "Technical Support",
          salary: {
            value: 7000,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 12,
          title: "Data Scientist",
          salary: {
            value: 11500,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 13,
          title: "Cloud Architect",
          salary: {
            value: 14000,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 14,
          title: "Blockchain Developer",
          salary: {
            value: 12500,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 15,
          title: "Security Analyst",
          salary: {
            value: 10500,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 16,
          title: "Business Analyst",
          salary: {
            value: 9500,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 17,
          title: "IT Consultant",
          salary: {
            value: 10200,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 18,
          title: "Software Engineer",
          salary: {
            value: 11000,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 19,
          title: "Digital Marketer",
          salary: {
            value: 9200,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
        {
          id: 20,
          title: "Content Strategist",
          salary: {
            value: 8900,
            currencies: [
              { label: "USD", coefficient: 1.5 },
              { label: "RUB", coefficient: 1 },
            ],
          },
        },
      ],
    };
  },
});
</script>
