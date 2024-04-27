<template>
    <div id="container">
        <Sidebar></Sidebar>
        <ClinicalAi v-show="view == 'Clinical MedAssist'"></ClinicalAi>
        <MainDashboard v-show="view == 'Overview'"></MainDashboard>
    </div>
</template>

<script setup>
const store = useDoctorStore();
const { view } = storeToRefs(store);
</script>

<style scoped lang="less">
#container {
    width: 100%;
    display: grid;
    grid-template-columns: 380px 1fr;
    position: fixed;
}
</style>