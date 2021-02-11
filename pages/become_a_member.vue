<template>
    <div class="max-w-7xl mx-auto spx-6 px-6 lg:px-8">
        <h1 class="text-2xl font-bold py-4">Become a Member</h1>
        <p class="py-2">
            Thank you for your interest in becoming a DES member! Firstly we would like to point out that <strong> you do not need to be a member to use the DES Slack, attend meetups and events, or to join the monthly society meeting and AGM. </strong> Membership is only required if you wish to vote, or use DES equipment and resources (like our YouTube channel or streaming tools.)
        </p>
        <p class="py-2">
            If you're still interested in becoming a member, please complete the form below and then e-transfer $20 to memberships@devedmonton.com. Your membership will be valid for one year from the date that your membership was received. After the transfer is sent and you fill out the form you will be added to a google group which contains all our meetings and AGM's you can attend.
        </p>
        <p class="py-2">
            Thank you to everyone on here for your continuing support and time. The Edmonton developer community is great, and we are looking forward to getting to know all our new members soon!
        </p>
        <div class="flex justify-center mt-4">
            <a
                href="https://docs.google.com/forms/d/e/1FAIpQLSdHuLt6NOuHIyLIXXdM6hf6TzlbG8VInLZe5E3M7pvwZrNHEQ/viewform?usp=sf_link"
            >
                <v-Button appearance="inverted">Become a Member</v-Button>
            </a>
        </div>
    </div>
</template>

<script>
import VButton from "~/components/VButton.vue";

export default {
    components: {
        VButton,
    },
};
</script>

<style lang="scss" scoped></style>
