<script>
export default {
  name: "Navigation",
  data() {
    return {
      should_show_mobile_navigation_content: false,
    };
  },
};
</script>

<template>
  <section class="navigation">
    <div class="logo">
      <a href="/" aria-label="Home">
        <img src="../assets/images/logo.png" alt="Toy Store" />
      </a>
    </div>
    <nav class="desktop-navigation">
      <ul>
        <li>
          <button @click="$emit('showHomepageContent')">Home</button>
        </li>
        <li>
          <button @click="$emit('showAboutContent')">About</button>
        </li>
        <li>
          <button @click="$emit('showToysContent')">Toys</button>
        </li>
        <li>
          <button @click="$emit('showContactForm')">Contact</button>
        </li>
      </ul>
    </nav>

    <div class="mobile-navigation__trigger">
      <button
        @click="
          should_show_mobile_navigation_content =
            !should_show_mobile_navigation_content
        "
        aria-label="menu"
      >
        <img src="../assets/images/hamburger.png" alt="" />
      </button>
    </div>

    <div
      class="mobile-navigation__content"
      v-if="should_show_mobile_navigation_content"
    >
      <nav class="mobile-navigation">
        <ul>
          <li>
            <button
              @click="
                $emit('showHomepageContent');
                should_show_mobile_navigation_content =
                  !should_show_mobile_navigation_content;
              "
            >
              Home
            </button>
          </li>
          <li>
            <button
              @click="
                $emit('showAboutContent');
                should_show_mobile_navigation_content =
                  !should_show_mobile_navigation_content;
              "
            >
              About
            </button>
          </li>
          <li>
            <button
              @click="
                $emit('showToysContent');
                should_show_mobile_navigation_content =
                  !should_show_mobile_navigation_content;
              "
            >
              Toys
            </button>
          </li>
          <li>
            <button
              @click="
                $emit('showContactForm');
                should_show_mobile_navigation_content =
                  !should_show_mobile_navigation_content;
              "
            >
              Contact
            </button>
          </li>
        </ul>
      </nav>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.navigation {
  background: #1c3344;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px;
  position: fixed;
  left: 0;
  right: 0;
  top: 0;

  .desktop-navigation {
    ul {
      display: flex;
      align-items: center;
      gap: 5px;
    }
    ul li {
      list-style-type: none;

      button {
        background: #1c3344;
        color: white;
        font-size: 1.3em;
        font-weight: bold;
        transition: 300ms all ease-in-out;
        padding: 5px 20px;
        border-radius: 40px;
        outline: none;
        border: none;
        cursor: pointer;

        &:active,
        &:hover,
        &:focus {
          background: white;
          color: #1c3344;
        }
      }
    }
  }

  .logo {
    a {
      img {
        max-width: 110px;
      }
    }
  }
}

.mobile-navigation__trigger {
  display: none;
}

.mobile-navigation__content {
  display: none;
}

@media (max-width: 890px) {
  .desktop-navigation {
    display: none;
  }
  .mobile-navigation__trigger {
    display: block;
  }

  .mobile-navigation__trigger button {
    background: #1c3344;
    outline: none;
    border: none;
    cursor: pointer;

    img {
      height: 40px;
      width: 40px;
    }
  }

  .mobile-navigation__content {
    display: block;
    position: fixed;
    top: 80px;
    background: #1c3344;
    color: white;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 1;
  }

  .mobile-navigation {
    display: flex;
    align-items: center;
    padding-top: 40px;
    background: #1c3344;

    ul {
      display: flex;
      align-items: center;
      flex-direction: column;
      justify-content: center;
      gap: 15px;
      width: 100%;
    }
    ul li {
      list-style-type: none;

      button {
        background: #1c3344;
        color: white;
        width: 180px;
        padding: 10px 20px;
        outline: 0;
        border: 0;
        font-size: 1.5em;
      }
    }
  }
}
</style>
