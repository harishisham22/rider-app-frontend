<template>
    <div class="pt-16">
        <h1 class="text-3xl font-semibold mb-4">UwUber</h1>
        <div class="overflow-hidden shadow sm:rounded-md max-w-sm mx-auto text-left">
            <div class="bg-white px-4 py-5 sm:p-6">
                <div class="bg-white px-4 py-5 sm:p-6">
                    <button
                        @click="handleStartDriving"
                        class="rounded-md border border-transparent bg-black py-2 px-4 text-sm font-medium text-white"
                        style="margin-right: 60px;">
                        Start Driving
                    </button>
                    <button
                        @click="handleFindARide"
                        class="rounded-md border border-transparent bg-black py-2 px-4 text-sm font-medium text-white">
                        Find A Ride
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import http from '@/helpers/http';
import { useRouter } from 'vue-router';


const router = useRouter()

const handleStartDriving = () => {
    http().get('/api/driver')
        .then((response) => {
            if (response.data.driver) {
                router.push({
                    name: 'standby'
                })
            } else {
                router.push({
                    name: 'driver'
                })
            }
        })
        .catch((error) => {
            console.error(error)
        })
}

const handleFindARide = () => {
    router.push({
        name: 'location'
    })
}
</script>