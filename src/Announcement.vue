<template>
    <div class="alert alert-info">
        <div v-if="announcement">
            <p>{{ announcement }}</p>
        </div>
        <div v-else>
            <p>No announcement yet.</p>
        </div>
    </div>
    
</template>

<script>
import { eventBus } from './main';
import Social from './Social.vue';

    export default {
        data() {
            return {
                announcement: null,        
            };
        },
        components: {
            appSocialShare: Social
        },
        created() {
            eventBus.$on('articleWasShared', (data) => {
                this.announcement = data.media
                console.log(data);
            });
        }
    }
</script>