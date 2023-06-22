<template>
    <div class="list-siswa">
        <table v-show="siswaList.length > 0" class="table table-responsive-md table-dark table-hover">
            <thead>
                <tr>
                    <th scope="col"><strong>No.Induk</strong></th>
                    <th scope="col"><strong>Nama</strong></th>
                    <th scope="col"><strong>Nilai</strong></th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="siswa in siswaList" :key="siswa.induk">
                    <td>{{ siswa.induk }}</td>
                    <td>{{ siswa.name }}</td>
                    <td>{{ siswa.score }}</td>
                </tr>
                <tr>
                    <th colspan="1" style="background-color: silver;"></th>
                    <th scope="col" style="background-color: silver; color: black;">Nilai Rata-Rata</th>
                    <td style="background-color: silver; color: black; text-decoration: underline;">{{ averageScore }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>


<script>
export default {
    props: {
        siswaList: {
            type: Array,
            default: () => []
        }
    },
    computed: {
        averageScore() {
            if (this.siswaList.length === 0) {
                return 0;
            }

            const totalScore = this.siswaList.reduce((acc, siswa) => {
                return acc + siswa.score;
            }, 0);

            const average = totalScore / this.siswaList.length;

            if (isNaN(average)) {
                return 0;
            }

            return average.toFixed(2);
        }
    }
};
</script>
