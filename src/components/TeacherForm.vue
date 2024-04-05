<template>
    <div class="w-full h-screen flex flex-row justify-center items-center bg-slate-300">
        <div class="container flex flex-col gap-5">
            <section class="flex flex-col gap-5">
                <h3>Include teacher</h3>
                <div class="flex flex-col items-center gap-5">
                    <div class="form__items"><label>First name:</label><input type="text" v-model="teacher.firstName">
                    </div>
                    <div class="form__items"><label>Last name:</label><input type="text" v-model="teacher.lastName">
                    </div>
                    <div class="form__items"><label>DNI/NIF:</label><input type="text" v-model="teacher.dni"></div>
                    <div class="form__items"><label>Subjects</label><input type="text" v-model="subject"><button
                            class="button" @click="handleSubject()">Include</button></div>
                    <div>
                        <ul>
                            <li v-for="(element, index) in teacher.subjects" :key="index">{{ element }}</li>
                        </ul>
                    </div>
                    <div class="flex flex-row gap-3">
                        <input type="checkbox" v-model="teacher.documentation" />
                        <p>Documentation provided</p>
                    </div>
                    <button class="button" @click="handleTeacher()">Include teacher</button>
                </div>
            </section>
            <section class="flex flex-col gap-5">
                <h3>Teachers List</h3>
                <table>
                    <thead>
                        <tr>
                            <th>First name</th>
                            <th>Last name</th>
                            <th>DNI/NIF</th>
                            <th>Subjects</th>
                            <th>Documentation</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="(element) in teachers" :key="element.dni">
                            <td>{{ element.firstName }}</td>
                            <td>{{ element.lastName }}</td>
                            <td>{{ element.dni }}</td>
                            <td>
                                <ul>
                                    <li v-for="(subject, index) in element.subjects" :key="index">{{ subject }}</li>
                                </ul>
                            </td>
                            <td>{{ element.documentation ? 'Yes' : 'No' }}</td>
                        </tr>
                    </tbody>
                </table>
            </section>
        </div>
    </div>
</template>

<script lang="ts" setup>
import { Ref, ref } from 'vue'

interface ITeacher {
    firstName: string,
    lastName: string,
    dni: string,
    subjects: Array<string>,
    documentation: boolean
}

const teacher: Ref<ITeacher> = ref({
    firstName: '',
    lastName: '',
    dni: '',
    subjects: [],
    documentation: false
})

const teachers: Ref<Array<ITeacher>> = ref([])

const subject: Ref<string> = ref('')

const handleSubject = () => {
    teacher.value.subjects.push(subject.value)
    subject.value = ''
}


const handleTeacher = () => {
    teachers.value.push(teacher.value)
    teacher.value = {
        firstName: '',
        lastName: '',
        dni: '',
        subjects: [],
        documentation: false
    }
}
</script>

<style scoped lang="scss">
h3 {
    @apply text-center text-2xl font-bold;
}

.button {
    @apply bg-blue-500 text-white font-bold py-2 px-4 rounded hover:bg-blue-700;
}

.form__items {
    @apply flex flex-row gap-3 items-center
}

td {
    @apply text-center bg-slate-100
}
</style>