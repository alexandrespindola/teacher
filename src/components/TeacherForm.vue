<template>
    <div class="w-full h-screen flex flex-row justify-center items-center bg-slate-300">
        <div class="container flex flex-col gap-5">
            <section class="flex flex-col gap-5">
                <h3>Include teacher</h3>
                <div class="flex flex-col items-center gap-5">
                    <div class="flex flex-row gap-3 items-center"><label>First name:</label><input type="text"></div>
                    <div class="flex flex-row gap-3 items-center"><label>Last name:</label><input type="text"></div>
                    <div class="flex flex-row gap-3 items-center"><label>DNI/NIF:</label><input type="text"></div>
                    <div class="flex flex-row gap-3 items-center"><label>Courses</label><input type="text"><button class="button" >Include</button></div>
                    <div class="flex flex-row gap-3">
                        <input type="checkbox" />
                        <p>Documentation provided</p>
                    </div>
                    <button class="button">Include teacher</button>
                </div>
            </section>
            <section class="flex flex-col gap-5">
                <h3>Teachers List</h3>
            </section>
        </div>
    </div>
</template>

<script lang="ts" setup>
</script>

<style scoped lang="scss">
h3 {
    @apply text-center text-2xl font-bold;
}
</style>