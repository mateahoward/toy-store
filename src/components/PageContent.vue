<script>
export default {
  name: "PageContent",
  props: ["title", "content"],
};
</script>

<template>
  <section class="section">
    <div class="section-content">
      <h1>{{ title }}</h1>

      <div class="section-content__paragraphs" v-html="content"></div>
    </div>

    <div class="section-cta">
      <button @click="$emit('showContactForm')">Contact us</button>
    </div>
  </section>
</template>

<style lang="scss">
.section {
  padding: 20px;
  display: flex;
  align-items: center;
  flex-direction: column;
  height: 100%;
}

.section-content {
  h1 {
    color: #1c3344;
  }

  &__paragraphs p {
    max-width: 400px;
    color: #1c3344;
  }
}

.section-cta {
  margin-top: 40px;

  button {
    outline: none;
    border: none;
    background: #1c3344;
    color: white;
    padding: 15px 35px;
    border-radius: 40px;
    transition: 300ms ease-in-out all;

    &:hover {
      padding: 15px 55px;
      background: white;
      color: #1c3344;
      border: 2px dashed #1c3344;
    }
  }
}
</style>
