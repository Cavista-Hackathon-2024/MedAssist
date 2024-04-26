<template>
  <div id="container">
    <div id="header">
      <h1>Welcome to <span>Med</span><span>Assist</span></h1>
      <p>Kindly choose the specific Demo for use case</p>
    </div>

    <div id="choose">
      <div class="card">
        <h3>
          Clinical Decision Support System (CDSS) - For Health professionals
        </h3>
        <p class="desc">
          Our next-generation AI enhanced CDSS portal.<br />The CDSS portal
          seamlessly integrates with your existing Electronic Health Record
          (EHR) system for evidence-based decision support at your fingertips.
        </p>
        <Button label="Click to Login" />
      </div>

      <div class="card">
        <h3>Patient Care Portal - For Patients</h3>
        <!-- <p class="for">For Patients</p> -->
        <p class="desc">
          The Patient Care Portal puts you at the center of your healthcare
          experience. This secure platform provides you with convenient 24/7
          access to a wealth of information and tools to manage your well-being.
        </p>
        <Button label="Click to Login" />
      </div>
    </div>
  </div>
</template>

<script setup>
import "primevue/resources/themes/aura-light-green/theme.css";
</script>

<style scoped lang="less">
#container {
  width: 100%;
  background: #f5f5f5;
}

#header {
  width: 100%;
  padding: 20px;
  text-align: center;
  padding-top: 80px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;

  h1 {
    font-size: 2rem;
    font-weight: 700;
    margin: 0;

    @media @desktop {
      font-size: 3rem;
    }
    span:first-of-type {
      color: #f9aa33;
      //color: #20c997;
    }
    span:last-of-type {
      color: #20c997;
      color: #f9aa33;
    }
  }

  p {
    font-size: 1rem;
    @media @desktop {
      font-size: 1.2rem;
    }
  }
}

#choose {
  width: 100%;
  max-width: 700px;
  padding: 20px;
  display: flex;
  flex-direction: column;
  gap: 30px 0;
  justify-content: center;
  align-items: center;
  margin: 0 auto;
  padding-bottom: 40px;

  @desktop {
    margin-top: 0px;
  }

  .card {
    padding: 30px 30px;
    background: #f2f2f2;
    background: white;
    border-radius: 15px;
    cursor: pointer;
    box-shadow: rgba(67, 71, 85, 0.27) 0px 0px 0.25em,
      rgba(90, 125, 188, 0.05) 0px 0.25em 1em;
    &:hover {
      //background: #e6e6e6;
      box-shadow: rgba(3, 102, 214, 0.3) 0px 0px 0px 3px;
    }
    .for {
      //margin-top: 10px;
      font-style: italic;
      font-weight: 200;
      color: ;
    }
    .desc {
      margin-top: 10px;
    }
    button {
      margin-top: 30px;
    }
  }
}
</style>
