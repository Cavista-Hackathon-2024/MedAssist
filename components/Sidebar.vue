<template>
  <div id="sidebar">
    <div id="doctor">
      <img src="@/assets/images/doc2.jpg" />
      <div class="profile">
        <h3>Dr. Akinleye Akanni</h3>
        <p>Department of Obstetrics and Gynaecology</p>
        <p>Specialty: Reproductive Endocrinology and Infertility (REI)</p>
      </div>
    </div>

    <div id="buttons">
      <button :class="{ active: view === 'Overview' }" @click="to('Overview')">
        Overview
      </button>
      <button
        :class="{ active: view === 'Clinical MedAssist' }"
        @click="to('Clinical MedAssist')"
      >
        Clinical MedAssist
      </button>
    </div>
  </div>
</template>

<script setup>
const store = useDoctorStore();
const { view } = storeToRefs(store);

const to = (where) => {
  view.value = where;
};
</script>

<style scoped lang="less">
#sidebar {
  height: 100dvh;
  background: #f5f5f5;
  border-right: 3px solid rgb(171, 171, 171);
}

#doctor {
  width: 100%;
  margin-top: 20px;
  height: max-content;
  padding: 20px;
  font-size: 15px;
  text-align: center;

  img {
    width: 80px;
    height: 80px;
    border-radius: 100%;
    object-fit: cover;
    object-position: top left;
    margin: 0 auto;
  }
  .profile {
    margin-top: 10px;
  }
}

#buttons {
  width: 100%;
  margin: 0 auto;
  padding: 0 10px;
  button {
    width: 100%;
    padding: 10px 20px;
    text-align: left;
    background: none;
    border: none;
    border-left: 3px solid teal;


    &.active {
      background: rgb(103, 209, 209);
      background: #d2d2d2;
    }
  }
}
</style>
