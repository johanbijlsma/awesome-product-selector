<script setup>
import Posterdata from '../data/posters.json'
import { ref } from 'vue'

function goToPrintType() {
  selection.value.selectedSize = ref(size.value.selectedASize)
  progress.value = ref(2)
}

const progress = ref(1)

const size = ref({
  selectedSizeParent: 'a_formaten',
  selectedASize: '',
  selectedBSize: '',
  selectedSpecialSize: '',
  Aformats: [
    {
      slug: 'abri',
      name: 'Abri - 1185 x 1750 mm',
      nullable: false,
      width: 1185,
      height: 1750,
      parent: 'a_formaten'
    },
    {
      slug: 'a0',
      name: 'A0 - 840 x 1189 mm',
      nullable: false,
      width: '840',
      height: '1189',
      parent: 'a_formaten'
    },
    {
      slug: 'a1',
      name: 'A1 - 594 x 840 mm',
      nullable: false,
      width: '594',
      height: '840',
      parent: 'a_formaten'
    },
    {
      slug: 'a2',
      name: 'A2 - 420 x 594 mm',
      nullable: false,
      width: '420',
      height: '594',
      parent: 'a_formaten'
    },
    {
      slug: 'a3',
      name: 'A3 - 297 x 420 mm',
      nullable: false,
      width: 297,
      height: 420,
      parent: 'a_formaten'
    },
    {
      slug: 'a4',
      name: 'A4 - 210 x 297 mm',
      nullable: false,
      width: '210',
      height: '297',
      parent: 'a_formaten'
    }
  ],
  Bformats: [
    {
      slug: 'b0',
      name: 'B0 - 1000 x 1400 mm',
      nullable: false,
      width: 1000,
      height: 1400,
      parent: 'b_formaten'
    },
    {
      slug: 'b1',
      name: 'B1 - 700 x 1000 mm',
      nullable: false,
      width: 700,
      height: 1000,
      parent: 'b_formaten'
    },
    {
      slug: 'b2',
      name: 'B2 - 500 x 700 mm',
      nullable: false,
      width: 500,
      height: 700,
      parent: 'b_formaten'
    },
    {
      slug: 'b3',
      name: 'B3 - 350 x 500 mm',
      nullable: false,
      width: '350',
      height: '500',
      parent: 'b_formaten'
    }
  ],
  specials: [
    {
      slug: 'a1_large',
      name: 'A1 large - 420 x 1189 mm',
      nullable: false,
      width: 420,
      height: 1189,
      parent: 'specials'
    },
    {
      slug: 'a2_large',
      name: 'A2 large - 297 x 840 mm',
      nullable: false,
      width: 297,
      height: 840,
      parent: 'specials'
    },
    {
      slug: 'a3_large',
      name: 'A3 large - 210 x 597 mm',
      nullable: false,
      width: 210,
      height: 597,
      parent: 'specials'
    },
    {
      slug: 'a4_large',
      name: 'A4 large - 148 x 420 mm',
      nullable: false,
      width: '148',
      height: 420,
      parent: 'specials'
    },
    {
      slug: 'b1_large',
      name: 'B1 large - 500 x 1400 mm',
      nullable: false,
      width: 500,
      height: 1400,
      parent: 'specials'
    },
    {
      slug: 'b2_large',
      name: 'B2 large - 350 x 1000 mm',
      nullable: false,
      width: 350,
      height: 1000,
      parent: 'specials'
    },
    {
      slug: 'b3_large',
      name: 'B3 large - 250 x 700 mm',
      nullable: false,
      width: 250,
      height: 700,
      parent: 'specials'
    }
  ]
})
const selection = ref({
  selectedSize: ''
})
const orders = ref([])
</script>

<template>
  <div class="container posters">
    <div class="intro">
      <h1 class="page-title">Posters</h1>
      <p class="intro-text">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsam, amet!
      </p>
      <hr class="divider" />
    </div>
    <template v-if="progress === 1">
      <aside class="step1">
        <h2 class="step-title">1. Size</h2>
      </aside>
      <div class="step-block step-1-block">
        <label for="a-formaten">
          <input
            type="radio"
            name="poster-size"
            id="a-formaten"
            value="a-formaten"
            checked
            v-model="size.selectedSizeParent"
          />A-formaten</label
        >
        <label for="b-formaten">
          <input
            type="radio"
            name="poster-size"
            id="b-formaten"
            value="b-formaten"
            v-model="size.selectedSizeParent"
          />B-formaten</label
        >
        <label for="specials"
          ><input
            type="radio"
            name="poster-size"
            id="specials"
            value="specials"
            v-model="size.selectedSizeParent"
          />
          Specials</label
        >
        <div class="size-dropdown">
          <template v-if="size.selectedSizeParent === 'a-formaten'">
            <select name="size" id="Asize" v-model="size.selectedASize">
              <option v-for="(Asizes, index) in size.Aformats" :key="index" :value="Asizes.slug">
                {{ Asizes.name }}
              </option>
            </select>
          </template>
          <template v-if="size.selectedSizeParent === 'b-formaten'">
            <select name="size" id="Bsize" v-model="size.selectedBSize">
              <option v-for="(Bsizes, index) in size.Bformats" :key="index" :value="Bsizes.slug">
                {{ Bsizes.name }}
              </option>
            </select>
          </template>
          <template v-if="size.selectedSizeParent === 'specials'">
            <select name="size" id="Specialsize" v-model="size.selectedSpecialSize">
              <option
                v-for="(specials, index) in size.Bformats"
                :key="index"
                :value="specials.slug"
              >
                {{ specials.name }}
              </option>
            </select>
          </template>
        </div>
      </div>
      <div class="button-container">
        <button class="primary" @click="goToPrintType">Go to Print type</button>
      </div>
    </template>
    <template v-if="progress.value === 2">
      <aside class="step2">
        <h2 class="step-title">2. Print Type</h2>
      </aside>
      <div class="step-block step-2-block">
        <label for="a-formaten">
          <input
            type="radio"
            name="poster-size"
            id="a-formaten"
            value="a-formaten"
            checked
            v-model="size.selectedSizeParent"
          />A-formaten</label
        >
        <label for="b-formaten">
          <input
            type="radio"
            name="poster-size"
            id="b-formaten"
            value="b-formaten"
            v-model="size.selectedSizeParent"
          />B-formaten</label
        >
        <label for="specials"
          ><input
            type="radio"
            name="poster-size"
            id="specials"
            value="specials"
            v-model="size.selectedSizeParent"
          />
          Specials</label
        >
        <div class="size-dropdown">
          <template v-if="size.selectedSizeParent === 'a-formaten'">
            <select name="size" id="Asize" v-model="size.selectedASize">
              <option v-for="(Asizes, index) in size.Aformats" :key="index" :value="Asizes.slug">
                {{ Asizes.name }}
              </option>
            </select>
          </template>
          <template v-if="size.selectedSizeParent === 'b-formaten'">
            <select name="size" id="Bsize" v-model="size.selectedBSize">
              <option v-for="(Bsizes, index) in size.Bformats" :key="index" :value="Bsizes.slug">
                {{ Bsizes.name }}
              </option>
            </select>
          </template>
          <template v-if="size.selectedSizeParent === 'specials'">
            <select name="size" id="Specialsize" v-model="size.selectedSpecialSize">
              <option
                v-for="(specials, index) in size.Bformats"
                :key="index"
                :value="specials.slug"
              >
                {{ specials.name }}
              </option>
            </select>
          </template>
        </div>
      </div>
      <div class="button-container">
        <button class="primary" @click="goToPrintType">Go to Print type</button>
      </div>
    </template>
    <pre>{{ posters }}</pre>
  </div>
</template>

<style>
.posters {
  display: grid;
  grid-auto-rows: auto;
  grid-template-columns: 1fr;
  gap: 1rem;
}

.intro-text {
  font-size: 1.5rem;
  font-style: normal;
  font-weight: 400;
  line-height: 2rem;
  letter-spacing: 0em;
  text-align: left;
}
aside {
  display: flex;
  align-items: center;
  background-color: var(--white);
  padding: 0.25rem;
}

hr.divider {
  border: none;
  border-bottom: 2px solid;
  border-bottom-color: var(--print-primary);
  margin: 0 0 1rem;
  width: 100%;
}
h2.step-title {
  font-size: 2.5rem;
  font-weight: 600;
  position: relative;
  display: inline-block;
  color: var(--print-primary);
}

.step-block {
  background-color: var(--print-grey);
  padding: 35px;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  gap: 3rem;
  align-items: flex-start;
  box-shadow: 0px 4px 4px 0px rgba(0, 0, 0, 0.25);
  border-radius: 10px;
  min-height: 100px;
  align-items: center;

  & label {
    font-size: 1.375rem;
  }
  & label:has(input[type='radio']:checked) {
    font-weight: 600;
  }
  & input[type='radio'] {
    margin-inline-end: 10px;
    appearance: none;
    &::before {
      content: '';
      display: block;
      width: 20px;
      height: 20px;
      border: 2px solid var(--black);
      border-radius: 50%;
      translate: 0 5px;
      transition: all 300ms ease-in;
    }
  }
  & input[type='radio']:checked {
    margin-inline-end: 10px;
    appearance: none;
    &::before {
      content: '';
      display: block;
      width: 20px;
      height: 20px;
      border: 2px solid var(--print-primary);
      outline: 2px solid var(--print-primary);
      outline-offset: 0.25rem;
      border-radius: 50%;
      background-color: var(--print-primary);
      box-shadow: 0 0 5px var(--print-primary) / 0.5;
    }
  }
  & .size-dropdown {
    width: 100%;
    & select {
      width: 100%;
    }
  }
}
.button-container {
  display: flex;
  justify-content: flex-end;
  gap: 1rem;
}

button.primary {
  appearance: none;
  background-color: var(--print-primary);
  color: var(--white);
  font-weight: 600;
  font-size: 1.375rem;
  padding: 0.5rem 1rem;
  border-radius: 7px;
  transition: all 0.3s ease-in-out;
  margin-block-start: 4rem;
  &:hover {
    background-color: var(--print-quaternary);
    cursor: pointer;
  }
}
@media screen and (min-width: 768px) {
  .posters {
    grid-template-columns: 250px 1fr;
  }
  .intro {
    grid-column: 2;
  }
  aside {
    grid-column: 1;
  }
  .step-block {
    grid-column: 2;
  }
  .button-container {
    grid-column: 2;
  }
}
</style>
