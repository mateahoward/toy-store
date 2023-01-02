<script>
export default {
  name: "ContactForm",
  data() {
    return {
      has_been_submitted: false,
    };
  },
};
</script>

<template>
  <section class="contact-form">
    <div class="contact-form__title">
      <h1>Contact form</h1>
    </div>
    <form
      @submit="has_been_submitted = !has_been_submitted"
      v-if="has_been_submitted == false"
    >
      <label>
        Name:
        <input type="text" name="Name" placeholder="e.g Sasha Smith" required />
      </label>
      <label>
        Email:
        <input
          type="email"
          name="Email"
          placeholder="e.g Sasha Smith"
          required
        />
      </label>

      <label>
        Message
        <textarea cols="50" rows="4" name="Message" required />
      </label>

      <button type="submit">Submit</button>
    </form>

    <section class="success" v-if="has_been_submitted == true">
      <p>Your message has been sent successfully.</p>

      <button @click="$emit('showHomepageContent')">Return to homepage</button>
    </section>
  </section>
</template>

<style lang="scss" scoped>
.contact-form {
  display: flex;
  flex-direction: column;
  align-items: center;
}

h1 {
  margin-bottom: 40px;
  color: #1c3344;
}
form {
  display: flex;
  flex-direction: column;
  align-items: center;

  label {
    display: flex;
    flex-direction: column;
    margin-bottom: 30px;
    text-align: left;
    width: 80%;
    font-size: 1.3em;
    font-weight: bold;
    color: #1c3344;
  }

  input {
    height: 40px;
  }

  input,
  textarea {
    outline: none;
    border: 1px solid grey;
    border-radius: 4px;
    text-indent: 10px;
    margin-top: 5px;
  }
}

button {
  outline: none;
  border: none;
  background: #1c3344;
  color: white;
  padding: 15px 45px;
  border-radius: 40px;
  transition: 300ms ease-in-out all;
  margin-top: 40px;

  &:hover {
    padding: 15px 55px;
    background: white;
    color: #1c3344;
    border: 2px dashed #1c3344;
  }
}
</style>
