<template>
    <div class="bg-white">
        <div class="max-w-7xl mx-auto px-4 pt-0 pb-8 sm:px-6 lg:px-12">
            <div
                class="px-6 py-4 bg-brand-primary rounded-lg md:py-8 md:px-8 lg:py-8 lg:px-16 sm:flex sm:flex-col sm:items-center sm:text-center"
            >
                <div class="">
                    <h2
                        class="text-2xl font-extrabold tracking-tight text-white sm:text-3xl"
                    >
                        Keep up to date with DES?
                    </h2>
                    <p class="mt-3 max-w-3xl text-lg leading-6 text-blue-100">
                        Enter your email below to sign up to our mailing list
                        and get information on DES news and events in your
                        inbox.
                    </p>
                </div>
                <div class="mt-8 sm:w-full sm:max-w-md">
                    <form
                        class="sm:flex"
                        name="newsletter-signup"
                        @submit.prevent="emailSignUp"
                    >
                        <input
                            id="emailAddress"
                            v-model="signUpEmail"
                            name="emailAddress"
                            type="email"
                            autocomplete="email"
                            required
                            class="w-full border-white px-4 py-2 placeholder-gray-500 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-indigo-700 focus:ring-white rounded-md"
                            placeholder="Enter your email"
                        />
                        <button
                            class="mt-3 w-full flex items-center justify-center px-4 py-2 border border-transparent shadow text-base font-medium rounded-md text-brand-primary bg-blue-100 hover:bg-white hover:text-brand-primary focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-indigo-700 focus:ring-white sm:mt-0 sm:ml-3 sm:w-auto sm:flex-shrink-0"
                            type="submit"
                        >
                            Sign Up
                        </button>
                    </form>
                </div>
                <div v-if="signUpSuccess" class="pt-4 text-lg text-blue-100">
                    <span>{{ signUpSuccess }}</span>
                </div>
                <div v-if="signUpError" class="pt-4 text-lg text-blue-100">
                    <span>{{ signUpError }}</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data: function () {
        return {
            signUpEmail: "",
            signUpSuccess: null,
            signUpError: null,
        };
    },
    methods: {
        emailSignUp: async function () {
            const self = this;
            self.signUpError = null;
            self.signUpSuccess = null;
            fetch("/.netlify/functions/newsletter-signup", {
                method: "POST",
                body: JSON.stringify({ email: this.signUpEmail }),
            })
                .then((res) => res.json())
                .then((data) => {
                    if (data.title === "Member Exists")
                        self.signUpError = "Your email is already on our list.";
                    else if (data.status === 400)
                        self.signUpError =
                            "Whoops! Looks like we couldn't add your email. Please try again or use our contact form.";
                    else if (data.signUpEmail)
                        self.signUpSuccess = `We have sent an email to ${data.signUpEmail} with a link to confirm your subscription.`;
                    self.signUpEmail = "";
                })
                .catch((err) => console.error(err));
        },
    },
};
</script>

<style lang="scss"></style>
