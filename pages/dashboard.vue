<template>
    <div id="container">
        <Sidebar></Sidebar>
        <ClinicalAi></ClinicalAi>
        <!-- <MainDashboard></MainDashboard> -->
    </div>
</template>

<script setup>

</script>

<style scoped lang="less">
#container {
    width: 100%;
    display: grid;
    grid-template-columns: 380px 1fr;
    position: fixed;
}
</style>