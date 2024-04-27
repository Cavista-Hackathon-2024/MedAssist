<template>
    <div id="container">
        <Sidebar></Sidebar>
        <MainDashboard></MainDashboard>
        <RightSidebar></RightSidebar>
    </div>
</template>

<script setup>

</script>

<style scoped lang="less">
#container {
    width: 100%;
    display: grid;
    grid-template-columns: 380px 1fr auto;
    position: fixed;
}
</style>