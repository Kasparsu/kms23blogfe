<script setup>
import axios from 'axios';
axios.defaults.withCredentials = true;
axios.defaults.withXSRFToken = true;
</script>

<template>
    <NuxtRouteAnnouncer />
    <MainNav></MainNav>
    <NuxtPage></NuxtPage>
</template>
