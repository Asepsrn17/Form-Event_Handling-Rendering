<template>
    <div class="card">
        <div class="card-body">
            <form @submit.prevent="submitForm">
                <div class="form-group">
                    <label for="student-induk">No Induk Siswa:</label>
                    <input v-model="student.induk" type="text" class="form-control" id="student-induk"
                        placeholder="Masukkan no induk siswa">
                </div>
                <div class="form-group">
                    <label for="student-name">Nama Siswa:</label>
                    <input v-model="student.name" type="text" class="form-control" id="student-name"
                        placeholder="Masukkan nama siswa">
                </div>
                <div class="form-group">
                    <label for="assignment-score">Nilai Tugas:</label>
                    <input v-model="student.score" type="number" class="form-control" id="assignment-score"
                        placeholder="Masukkan nilai tugas">
                </div>
                <button type="submit" class="btn btn-primary">Submit</button>
            </form>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            student: {
                induk: '',
                name: '',
                score: 0
            }
        };
    },
    methods: {
        submitForm() {
            this.$emit('submit', { ...this.student });
            this.student.induk = '';
            this.student.name = '';
            this.student.score = 0;
        }
    }
};
</script>
