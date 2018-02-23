<template>
    <div class="dropdown">
        <a id="dropdownMenuButton" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
            <i class="fas fa-bell"></i> {{ notifications.length }}
        </a>
        <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
            <a v-for="notification in notifications" class="dropdown-item">{{ notification }}</a>
        </div>
    </div>
</template>

<script>
    export default {
        data () {
            return {
                notifications: []
            }
        },

        mounted () {
            // Listen the notification when component ready!
            window.Echo.channel('pusher.demo.notification')
                .listen('SendNotification', (e) => this.notifications.unshift(e.data))

        }
    }
</script>
