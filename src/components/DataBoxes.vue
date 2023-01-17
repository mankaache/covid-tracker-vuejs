<template>
    <div class="grid md:grid-cols-2 gap-4 ">
        <!-- box1 -->
        <div class="shadow-md bg-blue-100 p-10 text-center rounded">
            <h3 class="text-3xl text-blue-900 font-bold mb-4">Cases</h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New:
                    {{numberWithCommas(stats.NewConfirmed)}}
                </span>
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total:
                    {{numberWithCommas(stats.TotalConfirmed)}}
                </span>
            </div>
        </div>
        <!-- box2 -->
        <div class="shadow-md bg-blue-200 p-10 text-center rounded">
            <h3 class="text-3xl text-blue-900 font-bold mb-4">Deaths</h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New:
                    {{numberWithCommas(stats.NewDeaths)}}
                </span>
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total:
                    {{numberWithCommas(stats.TotalDeaths)}}
                </span>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props:['stats'],
        methods: {
            numberWithCommas(x){
                return x.toLocaleString("en-US")
                
            }
        },
    }
</script>

<style scoped>

</style>