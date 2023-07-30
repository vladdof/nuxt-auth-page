<template>
    <div>
        <p
            v-if="loginError"
            style="color: var(--bs-form-invalid-color)"
        >
            {{ loginError }}
        </p>

        <form @submit.prevent="onSubmit">
            <text-field
                v-model="login"
                type-input="text"
                placeholder="Логин"
                label="Логин"
            />

            <text-field
                v-model="password"
                type-input="password"
                placeholder="Пароль"
                label="Пароль"
            />

            <the-button
                type="submit"
                class="btn btn-primary"
                text="Войти"
                :is-loading="loading"
            />
        </form>
    </div>
</template>

<script lang="ts">
import { useRouter } from 'nuxt/app';
import { defineComponent, ref } from 'vue';
import { delay } from '../lib/delay';

export default defineComponent({
    name: 'log-in',
    setup() {
        const loading = ref(false);
        const login = ref('admin');
        const password = ref('');
        const loginError = ref('');

        const router = useRouter();

        const validateData = () => {
            return (login.value === 'admin' && password.value === 'password');
        };

        const onSubmit = async () => {
            loginError.value = '';
            loading.value = true;
            await delay(2000);
            loading.value = false;

            if (validateData()) {
                router.push({ path: '/success' });
            } else {
                loginError.value = 'Данные для входа не совпадают';
            }
        };

        return {
            loading,
            login,
            password,
            loginError,
            onSubmit,
        };
    },
})
</script>
