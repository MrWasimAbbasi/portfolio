<template>
  <form id="contact-form" class="text-sm">
    <div class="flex flex-col mb-3">
      <label for="name" class="mb-3">_name:</label>
      <input type="text" id="name-input" @change="validateForm" :placeholder="name"
             class="p-2 mb-1 placeholder-slate-600">
      <span class="validation-message">{{ validationMessages.name }}</span>
    </div>
    <div class="flex flex-col mb-3">
      <label for="email" class="mb-3">_email:</label>
      <input type="email" id="email-input" @change="validateForm" name="email" :placeholder="email"
             class="p-2 mb-1 placeholder-slate-600">
      <span class="validation-message">{{ validationMessages.email }}</span>
    </div>
    <div class="flex flex-col">
      <label for="message" class="mb-3">_message:</label>
      <textarea id="message-input" @change="validateForm" name="message" :placeholder="message"
                class="placeholder-slate-600"></textarea>
      <span class="validation-message">{{ validationMessages.message }}</span>
    </div>
    <button id="submit-button" @click="submitForm(this)" type="button" class="py-2 px-4">submit-message</button>
  </form>
</template>

<script>


export default {
  name: 'ContactForm',
  props: {
    name: {
      type: String,
      required: true
    },
    email: {
      type: String,
      required: true
    },
    message: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      validationMessages: {
        name: '',
        email: '',
        message: ''
      },
    }
  },

  mounted() {

  },
  methods: {
    submitForm(event) {

      const isValid = this.validateForm();

      // Here the code to send the email
    },
    validateForm() {

      if (!this.name) {
        this.validationMessages.name = 'Name is required';
      } else {
        this.validationMessages.name = '';
      }

      if (!this.email) {
        this.validationMessages.email = 'Email is required';
      } else {
        this.validationMessages.email = '';
      }

      if (!this.message) {
        this.validationMessages.message = 'Message is required';
      } else {
        this.validationMessages.message = '';
      }

      // Return true if the form is valid, false otherwise
      return Object.values(this.validationMessages).every(message => !message);
    }
  }
}
</script>

<style>
.validation-message {
  color: red;
}

form {
  @apply font-fira_retina text-menu-text
}

input {
  background-color: #011221;
  border: 2px solid #1E2D3D;
  border-radius: 7px;

}

/* Change Autocomplete styles in Chrome*/
input:-webkit-autofill,
input:-webkit-autofill:hover,
input:-webkit-autofill:focus,
textarea:-webkit-autofill,
textarea:-webkit-autofill:hover,
textarea:-webkit-autofill:focus,
select:-webkit-autofill,
select:-webkit-autofill:hover,
select:-webkit-autofill:focus {
  -webkit-text-fill-color: rgb(190, 190, 190);
  transition: background-color 5000s ease-in-out 0s;
  border: 2px solid #607b96;
}

#message-input {
  background-color: #011221;
  border: 2px solid #1E2D3D;
  border-radius: 7px;
  resize: none;
  height: 150px;
  padding: 10px;
}

#submit-button {
  @apply font-fira_retina text-white text-sm;
  background-color: #1E2D3D;
  border-radius: 7px;
  margin-top: 20px;
  cursor: pointer;
}

#submit-button:hover {
  background-color: #263B50;
}

input:focus, #message-input:focus {
  outline: none;
  transition: none;
  border: 2px solid #607b96;
  box-shadow: #607b9669 0px 0px 0px 2px;
}

#contact-form {
  max-width: 370px;
  width: 100%;
}

@media (max-width: 1920px) {
  #contact-form {
    max-width: 320px;
    max-height: 400px;
  }

  #submit-button {
    /* width: 100%; */
    font-size: 12px;
  }

  textarea {
    font-size: 13px;
    max-height: 130px !important;
  }

  input {
    font-size: 13px;
  }
}
</style>