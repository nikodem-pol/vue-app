<script setup>
import { Field, Form, ErrorMessage } from 'vee-validate';
import { watch, ref, reactive } from 'vue'
import * as yup from 'yup';

const schema = yup.object({
    email: yup.string().required().email(),
    password: yup.string().required().min(8)
})

const credentials = ref({ name: '', password: '' })

watch(() => (credentials.value
), () => {
    console.log(credentials)
}, { deep: true })

</script>

<template>
    <div class="login-form-container">
        <Form @submit.prevent="" :validation-schema="schema">
            <h2>Sign in</h2>
            <div>
                <label for="email">Email</label>
                <Field name="email" v-model="credentials.name" />
                <ErrorMessage name="email" class="error-message"/>
            </div>

            <div>
                <label for="password">Password</label>
                <Field name="password" type="password" v-model="credentials.password"/>
                <ErrorMessage name="password" class="error-message"/>
            </div>

            <button id="sign-in" type="submit">Sign in</button>

            <button id="sign-up">Sign up</button>
        </Form>
    </div>
</template>

<style scoped>
Form {
    box-sizing: content-box;
    display: flex;
    flex-direction: column;
    gap: 1em;
    max-width: 30vw;
    border: 0px solid black;
    box-shadow: 8px 10px 18px -12px rgba(66, 68, 90, 1);
    border-radius: 1em;
    padding: 0 3em 2em;
    background-color: #f1f1f1;
}

Form > div {
    display: flex;
    flex-direction: column;
}

#sign-in {
    background-color: white;
    width: 6em;
    margin: auto
}

#sign-up {
    border: none;
    color: rgb(52, 141, 241);
    font-size: large;
}

.error-message {
    color: red;
    font-size: small;
}

.login-form-container {
    width: 100%;
    display: flex;
    justify-content: center;
}



</style>