<template>
  <v-container class="mx-auto">
    <v-row align="center" justify="center">
      <v-col>
        <v-row align="center" justify="center">
          <FormulateForm
            v-model="formValues"
            class="pa-12 my-6 form"
            style="border: 1px solid #a8a8a8;"
          >
            <h2>Register</h2>
            <v-divider />
            <p class="mt-4">
              Please make sure all information is filled out before you click
              the 'Register' button.
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
              placeholder="Select an animal"
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
                  name="Password"
                  label="Password"
                  placeholder="Your password"
                  validation="required"
                />
              </v-col>
              <v-col cols="6">
                <FormulateInput
                  type="password"
                  name="password_confirm"
                  label="Confirm your password"
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
              name="sample"
              label="Sample color input"
              placeholder="Sample color placeholder"
              help="Sample color help text"
              validation="required"
              value="#3eaf7c"
              error-behavior="live"
            />

            <FormulateInput
              type="textarea"
              v-model="textareaValue"
              label="Tell us about yourself"
              validation="required|max:100, length"
              :help="
                `Keep it under 100 characters. ${100 -
                  textareaValue.length} left.`
              "
            />

            <v-btn
              class="primary white--text py-2 my-3"
              style="border-radius: 5px;"
            >
              Register
            </v-btn>
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
        sample: "",
        email: "",
        headshot: "",
        file: ""
      },
      value: [],
      animalOptions: {
        hello: "Hello",
        whatsup: "Whatsup",
        hey: "Hey",
        hola: "Hola"
      },
      textareaValue: "",
      selectedAnimal: "",
      currentDate: new Date().toISOString().substr(0, 10)
    };
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

.formulate-input-element.formulate-input-element--color input {
  padding: 15px;
}
</style>
