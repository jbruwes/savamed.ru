<template></template>

<script setup lang="js">
import { inject } from "vue";
import { useI18n } from "vue-i18n";

const { id } = defineProps(["id"]),
    pages = inject("pages"),
    the = pages[id],
    { t } = useI18n({
        messages: {
            en: {
            },
            ru: {
            }
        }
    });
</script>