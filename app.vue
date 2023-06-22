<template>
  <div>
    <Form @submit="addSiswa" />
    <SiswaList :siswaList="siswaList" />
  </div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
import Form from "~/components/Form/Form.vue"
import SiswaList from "~/components/ListSiswa/SiswaList.vue"

export default {
  components: {
    Form,
    SiswaList
  },
  data() {
    return {
      siswaList: []
    };
  },
  methods: {
    addSiswa(siswa) {
      if (siswa.induk.trim() === '' || siswa.name.trim() === '' || isNaN(siswa.score)) {
        alert('Data siswa tidak valid');
        return;
      }
      this.siswaList.push(siswa);
    }

  }
};
</script>

<style>
body {
  background-color: slateblue;
  color: white;
}

.card {
  width: 18rem;
  margin: 0 auto;
  margin-top: 100px;
}

.form-group label {
  color: black;
}

.form-group {
  margin-bottom: 20px;
}

.list-siswa {
  max-width: 50rem;
  margin: 0 auto;
  margin-top: 50px;
}
</style>
