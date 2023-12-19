<template>
  <div class="container posters">
    <div class="intro">
      <h1 class="page-title">Business-cards</h1>
      <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsam, amet!</p>
      <hr class="divider" />
    </div>
    <aside class="step1">
      <h2 class="step-title">1. Size</h2>
    </aside>
    <div class="step-block step-1-block">
      <input type="radio" name="a-formaten" id="a-formaten" checked />
      <label for="a-formaten">A-formaten</label>
      <input type="radio" name="b-formaten" id="b-formaten" />
      <label for="b-formaten">B-formaten</label>
      <input type="radio" name="specials" id="specials" /> <label for="specials">Specials</label>
    </div>
  </div>
</template>

<style>
.posters {
  display: grid;
  grid-auto-rows: auto;
  grid-template-columns: 1fr;
  gap: 1rem;
}

aside {
  /* grid-column: 1; */
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
  padding-block: 1rem;
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
  }
}
</style>
