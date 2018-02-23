<template>
    <div>
        <button @click="sendNotification" class="btn btn-primary">
            <i class="fas fa-paper-plane"></i> Send Notification
        </button>
        <span v-if="isSuccess" class="text-success">Done!</span>
    </div>
</template>

<script>
    export default {
        data () {
            return {
                isSuccess: false
            }
        },

        methods: {
            /**
             * Handle send notification using axios.
             */
            sendNotification: function () {
                this.isSuccess = false;

                axios.post('/send-notification')
                    .then(response => this.isSuccess = true)
                    .catch(errors => console.log(errors))
            }
        }
    }
</script>
