<template>
  <div id="main-dashboard">
    <h1>{{ view }}</h1>

    <div id="summary">
      <div class="card">
        <h3>Appointments</h3>
        <p>17</p>
      </div>
      <div class="card">
        <h3>In Patients</h3>
        <p>11</p>
      </div>
      <div class="card">
        <h3>Out Patients</h3>
        <p>29</p>
      </div>
    </div>

    <div id="ai-summary">
      <h2>Priority Action Board <span>AI</span></h2>
      <div class="timeline">
        <h3>2PM Biopsy Reminder</h3>
        <p>
          This is a friendly reminder that your 2:00 PM (WAT) appointment today
          with in-patient Ogunsola Abosede is for a scheduled endometrial
          biopsy. The procedure details and any pre-appointment instructions are
          available for review in the patient's care portal.
        </p>
        <Button label="See Patient Info" outlined  />
      </div>
      <Divider />
      <div class="timeline">
        <h3>IUD Consultation: Adaeze Ngozi</h3>
        <p>
          Outpatient Adaeze Ngozi has submitted a request today to explore the
          possibility of an IUD insertion. This could be for initiating a new
          form of birth control or replacing an existing one that's nearing its
          expiration date. A follow-up appointment to discuss IUD options and
          suitability for Adaeze would be the next step.
        </p>
        <Button label="See Patient Info" outlined  />
      </div>
    </div>

    <PatientList></PatientList>

  </div>
</template>

<script setup>
const store = useDoctorStore();
const { view } = storeToRefs(store);
</script>

<style scoped lang="less">
#main-dashboard {
  width: 100%;
  height: 100dvh;
  overflow-y: auto;
  padding: 30px;
  h1 {
    font-size: 40px;
  }
}

#summary {
  margin-top: 40px;
  display: flex;
  justify-content: flex-start;
  align-items: center;
  gap: 0 10px;

  .card {
    width: 250px;
    height: 150px;
    background: rgb(202, 225, 225);
    padding: 20px;
    text-align: center;
    border-radius: 20px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    p {
      font-size: 40px;
      font-weight: 800;
    }
  }
}

#ai-summary {
  margin-top: 70px;
  background: #f5f5f5;
  padding: 20px;
  border-radius: 20px;
  max-width: 800px;
  h2 {
    //text-align: center;
    padding-bottom: 20px;
    font-size: 20px;
  }
  h2 > span {
    padding: 2px 20px;
    background: rgb(202, 225, 225);
    border-radius: 10px;
  }

  .timeline {
    max-width: 800px;
    margin-top: 10px;
    p {
      margin-top: 5px;
    }
    button {
      margin-top: 20px;
    }
  }
}
</style>
