<template>
  <div>

    <div> 

      <div class="con-belt"></div>

      <div class="banner">
        <img src="~/assets/img/plants-banner.png" alt="PostCity Banner" />	
      </div>
      
      <div class="header-box">
        <div class="intro header">
          <h3>THE FACTS</h3>
          <div class="arrow-down"></div>
          <div class="arrow-down"></div>
          <div class="arrow-down"></div>
        </div>
      </div>
      
      <div class="text-box mb-4">
        <h3>What is the Institute of Digital Sciences (IDSA)?</h3>
        <p>Lorem lorem lorem ipsum</p>
      </div>

      <div class="full">
        <img src="~/assets/img/orange2_sonia_litwin_ccby.png" alt="Orange Wall" class="" />	
        <div class="con-belt"></div>
      </div>

      <h4 class="text-2xl uppercase mb-4 font-mono text-blue-300">Without further ado:</h4>

      <h3 class="text-3xl uppercase mb-4 font-mono text-blue-300">IDSA x Ars Electronica Present ...</h3>

      <div
        class="graphic sticky top-0 border mt-20 flex items-center justify-center text-8xl"
      >
        <!--{{ activeStepIdSticky }}-->
        <img src="~/assets/img/cnv-blt-vrt.png" alt="Conveyor Belt" class="bg-img" />	
      </div>

      <Scrollama
        :offset="0.6"
        class="relative"
        @step-enter="stepEnterHandlerSticky"
      >
        <div
          v-for="step in stepsSticky"
          :key="step.id"
          :data-step-id="step.id"
          class="cnv-blt-1 step my-64 h-48 w-48 mx-auto bg-yellow-300 border border-black flex justify-center items-center text-4xl uppercase mb-4 font-mono"
          @step-enter="stepEnterHandlerSticky"
        >
          <span class="text-9xl text-gray-600">{{ step.id }}</span> {{ step.text }}
        </div>
      </Scrollama>

    </div>

    <div class="header-box">
      <div class="info header">
        <h3>THE IDEAS</h3>
        <div class="arrow-down"></div>
        <div class="arrow-down"></div>
        <div class="arrow-down"></div>
      </div>
    </div>
    
    <div class="text-box mb-4">
      <h3>How will IDSA teach?</h3>
      <p>Lorem lorem lorem ipsum</p>
    </div>^

    <div class="full">
      <img src="~/assets/img/RoboticsTopic_sonia_litwin_ccby.png" alt="Orange Wall" class="" />	
      <div class="con-belt"></div>
    </div>

    <div class="flex mb-8"> 

      <div
        class="graphic flex-1 sticky top-0 bg-gray-300 border border-black mt-20 flex items-center justify-center text-8xl"
      >
        {{ activeStepIdSticky2 }}
      </div>
      <Scrollama
        :offset="0.6"
        class="flex-1"
        @step-enter="stepEnterHandlerSticky2"
      >
        <div
          v-for="step in stepsSticky2"
          :key="step.id"
          :data-step-id="step.id"
          class="my-64 h-48 w-48 mx-auto bg-yellow-300 border border-black flex justify-center items-center"
          @step-enter="stepEnterHandlerSticky2"
        >
          Discipline {{ step.id }}
        </div>
      </Scrollama>
    </div>

    <div class="header-box">
      <div class="intro header">
        <h3>THE FOUNDING LAB</h3>
        <div class="arrow-down"></div>
        <div class="arrow-down"></div>
        <div class="arrow-down"></div>
      </div>
    </div>
    
    <div class="text-box mb-4">
      <h3>Topic Groups</h3>
      <p>Lorem lorem lorem ipsum</p>
    </div>

    <Scrollama
        :offset="0.6"
        @step-enter="stepEnterHandler"
        @step-exit="stepExitHandler"
      >
        <div
          v-for="step in steps"
          :key="step.id"
          :data-step-id="step.id"
          class="my-64 border border-black flex justify-center items-center"
          :class="{ 'bg-yellow-300': activeStepId === step.id }"
        >
          <img :src="step.image" :alt="step.id" class="topic-group-steps" />
        </div>
    </Scrollama>

    <div class="header-box">
      <div class="summary header">
        <h3>THE NEXT STEPS</h3>
        <div class="arrow-down"></div>
        <div class="arrow-down"></div>
        <div class="arrow-down"></div>
      </div>
    </div>
    
    <div class="text-box mb-4">
      <h3>Lorem ipsum</h3>
      <p>Lorem lorem lorem ipsum</p>
    </div>

    <div class="text-box mb-4 endnotes">
      <h3>Lorem ipsum</h3>
      <p>Lorem lorem lorem ipsum</p>
    </div>

  </div>
</template>

<script>
export default {
  data () {
    return {
      steps: [{ id: '1', image: require('../assets/img/topicgroup-ai.png') }],
      stepsSticky: [{ id: '75', text: 'Students' }, { id: '21', text: 'Fellows' }, { id: '6', text: 'Topics' }, { id: '1', text: 'New University' }],
      stepsSticky2: [{ id: 'I' }, { id: 'II' }, { id: 'III' }, { id: 'IV' }],
      activeStepId: null,
      activeStepIdSticky: 'A',
      activeStepIdSticky2: 'I'
    }
  },
  methods: {
    stepEnterHandler ({ element, direction, index }) {
      console.log('step-enter', { element, direction, index })
      this.activeStepId = element.dataset.stepId
    },
    stepEnterHandlerSticky ({ element, direction, index }) {
      console.log('step-enter', { element, direction, index })
      this.activeStepIdSticky = element.dataset.stepId
    },
    stepEnterHandlerSticky2 ({ element, direction, index }) {
      console.log('step-enter', { element, direction, index })
      this.activeStepIdSticky2 = element.dataset.stepId
    },
    stepExitHandler ({ element, direction, index }) {
      console.log('step-exit', { element, direction, index })
      this.activeStepId = null
    }
  }
}
</script>

<style scoped>
.graphic {
  height: 80vh;
}

.full {
  display: block;
  width: 100%;
  height: 100%;
}

.bg-img {
  width: 245px;
}

.header {
  background-color: #fff;
  color: #000;
  font-weight: bold;
  font-size: 3em;
  padding: 10px;

  border: 10px solid #000
}

  .header-box {
    background-color: #fff;
    padding: 10px;
    margin-bottom: 20px;
  }

.text-box {
  margin: 20px 0;
}

  .text-box h3 {
    font-size: 2em;
    margin-bottom: 10px;
    text-align: left;
    font-weight: bold;
    color: #ed820e;
  }

  .text-box p {
    font-size: 1.2em;
    text-align: left;
  }

.arrow-down {
  width: 0; 
  height: 0; 
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
  
  border-top: 20px solid #000;

  margin: 5px;
}


.banner {
  margin-bottom: 100px;
}

.intro {
  
}

.cnv-blt-1 {
  margin-bottom: 100px;
}

.summary {
  
}

.endnotes {
  margin-bottom: 200px;
}

.topic-group-steps {
  width: 100%;
  height: 100%;
}

.con-belt {
  width: 100%;
  height: 60px;
  margin-left: 60px;
  color: #f72585;
  background: linear-gradient(90deg, currentColor 50%, #0000 0) 0 0%,
    linear-gradient(-90deg, currentColor 50%, #0000 0) 50%,
    linear-gradient(90deg, currentColor 50%, #0000 0) 0 100%;
  background-size: 10px calc(100% / 3);
  background-repeat: repeat-x;
  animation: roll 0.25s infinite linear;
}

.con-belt-v {
  width: 60px;
  height: 100%;
  margin-left: 60px;
  color: #f72585;
  background: linear-gradient(0deg, currentColor 50%, #0000 0) 0 0%,
    linear-gradient(0deg, currentColor 50%, #0000 0) 50%,
    linear-gradient(0deg, currentColor 50%, #0000 0) 0 100%;
  background-size: 10px calc(100% / 3);
  background-repeat: repeat-y;
  animation: roll 0.25s infinite linear;
}

@keyframes roll {
  100% {
    background-position: -8px 0%, -8px 50%, -8px 100%;
  }
}
</style>