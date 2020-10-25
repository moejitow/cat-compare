<template>
    <div class="countdown">
        <!-- TODO: progress bar should always be same width -->
        <v-progress-linear style="width: 50em" :value=currentTime :buffer-value=time></v-progress-linear>
        <span v-if="!timeout">
            {{ currentTime }}
        </span>
        <span v-else>Time is up!</span>
    </div>
</template>

<script>
export default {
    name: 'Countdown',
    props: {
        time: {
            type: Number,
            required: true
        }
    },
    data: function() {
        return {
            currentTime: 0,
            timeout: false
        }
    },
    watch: {
        currentTime: {
            handler(value) {

                if (value < this.time) {
                    setTimeout(() => {
                        this.currentTime++;
                    }, 1000);
                }
                else {
                    this.timeout = true
                }

            },
            immediate: true // This ensures the watcher is triggered upon creation
        }
    }
}
</script>