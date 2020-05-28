<template>
  <v-container class="mx-auto">
    <v-row align="center" justify="center">
      <v-col>
        <v-row align="center" justify="center">
          <FormulateForm
            v-model="formValues"
            name="registration"
            class="pa-12 my-6 form white"
            style="border: 1px solid #a8a8a8;"
            @submit="submitForm"
          >
            <h2>Account Registration</h2>
            <v-divider />
            <p class="mt-4">
              Please make sure all information is filled out before you click
              the 'Submit' button.
            </p>
            <FormulateInput
              name="name"
              label="What is your first and last name? *"
              validation="required"
              class="mt-6"
              placeholder="John Doe"
            />
            <v-row>
              <v-col cols="6">
                <!--                <FormulateInput-->
                <!--                  type="number"-->
                <!--                  name="age"-->
                <!--                  label="What is your age? *"-->
                <!--                  validation="required|number|max:100"-->
                <!--                  placeholder="21"-->
                <!--                />-->
                <FormulateInput
                  type="date"
                  name="Date of Birth"
                  label="Date of Birth"
                  placeholder="Sample date placeholder"
                  validation="required"
                  min="1920-01-01"
                  :max="currentDate"
                />
              </v-col>
              <v-col cols="6">
                <FormulateInput
                  type="email"
                  name="email"
                  label="What is your email? *"
                  validation="required"
                  placeholder="abcd1234@express.com"
                />
              </v-col>
            </v-row>
            <FormulateInput
              type="select"
              name="favorite animal"
              :options="animalOptions"
              v-model="selectedAnimal"
              label="What is your favorite animal?*"
              placeholder="Select an animal..."
              validation="required"
            />
            <v-row>
              <v-col cols="6">
                <FormulateInput
                  type="file"
                  name="file"
                  label="Select your documents to upload"
                  help="Select one or more PDFs to upload"
                  validation="mime:application/pdf"
                  multiple
                />
              </v-col>
              <v-col cols="6">
                <FormulateInput
                  type="image"
                  image-behavior="file"
                  name="headshot"
                  label="Select an image to upload"
                  help="Select a png, jpg or gif to upload."
                  validation="mime:image/jpeg,image/png,image/gif"
                />
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="6">
                <FormulateInput
                  type="password"
                  name="password"
                  label="Password"
                  placeholder="Your password..."
                  validation="required|min:8, length"
                  help="Password must be at least 8 characters"
                />
              </v-col>
              <v-col cols="6">
                <FormulateInput
                  type="password"
                  name="password_confirm"
                  label="Confirm password..."
                  validation="required|confirm"
                  placeholder="Confirm password"
                  validation-name="Confirmation"
                />
              </v-col>
            </v-row>
            <!--            <v-row>-->
            <!--              <v-col cols="12">-->
            <!--                <FormulateInput-->
            <!--                  v-model="value"-->
            <!--                  :options="checkboxOptions"-->
            <!--                  type="checkbox"-->
            <!--                  label="This is a label for all the options"-->
            <!--                  validation="required"-->
            <!--                />-->
            <!--                {{ value }}-->
            <!--              </v-col>-->
            <!--            </v-row>-->

            <FormulateInput
              type="color"
              name="fontColor"
              label="Font color"
              placeholder="Font color..."
              help="Selected font color..."
              validation="required"
              value="#3eaf7c"
              error-behavior="submit"
            />

            <div
              id="color-box"
              :style="{ backgroundColor: formValues.fontColor }"
            ></div>

            <FormulateInput
              type="textarea"
              v-model="textareaValue"
              label="Tell us about yourself"
              validation="max:100, length"
              :help="
                `Keep it under 100 characters. ${100 -
                  textareaValue.length} left.`
              "
              class="mt-3"
            />

            <v-row>
              <v-col cols="4">
                <FormulateInput
                  type="submit"
                  id="submit-btn"
                  class="primary white--text py-2 my-3"
                  style="border-radius: 5px;"
                />
              </v-col>
              <v-col cols="4">
                <FormulateInput
                  type="button"
                  label="Reset"
                  class="error white--text py-2 my-3"
                  style="border-radius: 5px;"
                  @click="resetForm"
                />
              </v-col>
            </v-row>
          </FormulateForm>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Form",
  components: {},
  data() {
    return {
      formValues: {
        name: "",
        fontColor: "",
        email: "",
        headshot: "",
        file: ""
      },
      value: [],
      animalOptions: {
        dog: "Dog",
        shark: "Shark",
        cat: "Cat",
        Kangaroo: "Kangaroo"
      },
      textareaValue: "",
      selectedAnimal: "",
      currentDate: new Date().toISOString().substr(0, 10)
    };
  },
  methods: {
    submitForm(data) {
      alert("data", data);
    },
    resetForm() {
      this.$formulate.reset("registration");
    }
  }
};
</script>

<style>
.form {
  border-radius: 5px;
}

.formulate-input-wrapper .formulate-input-label {
  font-weight: bold;
}

.formulate-input-element input,
.formulate-input-element textarea,
.formulate-input-element select {
  border: 1px solid gray;
  border-radius: 5px;
  padding: 10px 2px;
  width: 100%;
}

.formulate-input-element button {
  width: 100%;
  font-weight: bold;
}

.formulate-input-element.formulate-input-element--color input {
  padding: 15px;
}

.formulate-input-error {
  color: #c62828;
}

#color-box {
  height: 25px;
  border: 1px solid black;
  border-radius: 5px;
}
</style>
