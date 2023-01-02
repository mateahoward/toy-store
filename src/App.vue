<script>
import Navigation from "./components/Navigation.vue";
import PageContent from "./components/PageContent.vue";
import ContactForm from "./components/ContactForm.vue";

import data from "./assets/data/data.json";
export default {
  components: {
    Navigation,
    PageContent,
    ContactForm,
  },
  data() {
    return {
      page_title: "",
      page_content: "",
      should_show_contact_form: false,
    };
  },
  mounted() {
    this.showHomepageContent();
  },
  methods: {
    scrollToTop() {
      window.scrollTo({ top: 0, behavior: "smooth" });
    },
    animateContent() {
      if (document.querySelector(".page-content-wrapper")) {
        this.removeAnimation();
        setTimeout(() => {
          this.scrollToTop();
          this.applyAnimation();
        }, 400);
      }
    },

    applyAnimation() {
      document.querySelector(".page-content-wrapper").classList.add("animated");
    },

    removeAnimation() {
      document
        .querySelector(".page-content-wrapper")
        .classList.remove("animated");
    },
    showHomepageContent() {
      this.animateContent();
      setTimeout(() => {
        this.page_title = this.homepage.title;
        this.page_content = this.homepage.content;

        this.should_show_contact_form = false;
      }, 400);
    },
    showAboutContent() {
      this.animateContent();
      setTimeout(() => {
        this.page_title = this.about.title;
        this.page_content = this.about.content;
        this.should_show_contact_form = false;
      }, 400);
    },
    showToysContent() {
      this.animateContent();
      setTimeout(() => {
        this.page_title = this.toys.title;
        this.page_content = this.toys.content;
        this.should_show_contact_form = false;
      }, 400);
    },
    showContactForm() {
      this.animateContent();
      setTimeout(() => {
        this.page_title = "";
        this.page_content = "";
        this.should_show_contact_form = true;
      }, 400);
    },
  },
  computed: {
    currentYear() {
      const date = new Date();
      return date.getFullYear();
    },
    homepage() {
      return data.homepage;
    },
    about() {
      return data.about;
    },
    toys() {
      return data.toys;
    },
  },
};
</script>

<template>
  <a href="#main" class="skip-to-main">Skip to main</a>

  <Navigation
    @showHomepageContent="showHomepageContent()"
    @showAboutContent="showAboutContent()"
    @showToysContent="showToysContent()"
    @showContactForm="showContactForm()"
  ></Navigation>
  <main class="page" id="main">
    <section class="page-content-wrapper">
      <template v-if="should_show_contact_form == false">
        <PageContent
          :title="page_title"
          :content="page_content"
          @showContactForm="showContactForm()"
        ></PageContent>
      </template>
      <template v-else>
        <ContactForm @showHomepageContent="showHomepageContent()"></ContactForm>
      </template>
    </section>
    <section class="page-background"></section>
  </main>
  <footer>
    <p>© Toy Store Ltd, 1997 - {{ currentYear }}</p>
  </footer>
</template>

<style lang="scss">
.skip-to-main {
  position: absolute;
  left: 9999px;

  &:focus {
    position: fixed;
    top: 20px;
    left: 40%;
    display: block;
    background: #efba70;
    color: #1c3344;
    z-index: 99;
    padding: 10px 55px;
  }
}

main {
  background: linear-gradient(
    90deg,
    rgba(66, 159, 169, 1) 0%,
    rgba(104, 202, 212, 1) 35%,
    rgba(92, 189, 200, 1) 100%
  );
  width: 100%;
}
.page {
  min-height: 620px;
  width: 100%;
  display: flex;
  padding-top: 20px;
  padding-bottom: 20px;
  margin-top: 90px;
  &-content-wrapper {
    width: 50%;
    margin-top: 60px;
    position: relative;
  }

  &-background {
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    background-image: url("./assets/images/background.png");
    width: 50%;
    box-shadow: -4px 0px 3px 4px #63c4ce inset;
  }
}

footer {
  position: relative;
  bottom: 0;
  padding: 50px;
  left: 0;
  right: 0;
  background: #1c3344;

  p {
    color: white;
  }
}
@keyframes move-to-top {
  from {
    top: 120px;
    opacity: 0;
  }
  to {
    top: 0;
    opacity: 1;
  }
}

.animated {
  animation-name: move-to-top;
  animation-duration: 0.8s;
}

@media (max-width: 890px) {
  .page {
    flex-direction: column-reverse;
    align-items: center;

    &-content-wrapper {
      width: 90%;
      margin-bottom: 60px;
      margin-top: 0;
    }
    &-background {
      width: 100%;
      height: 500px;
    }
  }
}
</style>
