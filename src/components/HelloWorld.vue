<template>
  <div class="hello">
    <h1 v-if="isNameShown">
      Halo, Nama Saya <span v-html="firstName"></span> {{ lastName }}
    </h1>
    <p>
      <input type="text" name="firstName" v-model="firstName">
      <input type="text" name="lastName" v-model="lastName">
      <input type="text" name="city" v-model="address.city">
      <input type="text" name="city" v-model="address.province">
      <br>
      Masukkan Tanggal Lahir anda: 
      <input type="number" v-model="myBirthYear">
    </p>
    <p>
      Saya tinggal di {{ address.city }}, {{ address.province }}
    </p>
    <p>
      Tahun depan, saya berumur {{ age + 1 }} tahun.
    </p>
    <p>
      Saya {{ work ? 'Bekerja' : 'Tidak Bekerja' }}
    </p>
    <p>
      Saya
      <span v-if="age < 10 && age > 0"> masih anak kecil</span>
      <span v-else-if="age < 20 && age > 10"> sudah remaja</span>
      <span v-else> tua</span>
    </p>
    <p>
      <ul>
        <li v-for="mantan in daftarMantan" :key="mantan.id">
          Teteh {{ mantan.namaMantan }}
        </li>
      </ul>
    </p>
    <p>
      <a v-bind:href="facebookUrl" :title="title">Facebook Saya</a>
      <br>
      <button :disabled="buttonState">
        Klik Saya Dong
      </button>
      <button v-if="buttonState">
        Klik Saya Dong
      </button>
      <button @click="showName()">
        Toggle Nama 
      </button>
    </p>
    <p>
      Umur saya 
      {{ getMyAge }}
      {{ getAddressData }}
    </p>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      firstName: "Galih",
      lastName: "Pratama",
      work: false,
      age: 23,
      myBirthYear: 1994,
      address: {
        city: "Cimahi",
        province: "Jawa Barat",
        country: "Indonesia"
      },
      facebookUrl: "https://facebook.com/pratamagalih",
      title: "Situs Facebook Galih Pratama",
      buttonState: false,
      isNameShown: true,
      daftarMantan: [
        { id: 1, namaMantan: "Aurel" },
        { id: 2, namaMantan: "Nuhha" },
        { id: 3, namaMantan: "Kirana" }
      ],
      rumah: [],
      isRumahShown: false
    };
  },
  methods: {
    showName() {
      this.isNameShown = !this.isNameShown;
    },
    getCurrentYear() {
      let currentYear = new Date().getFullYear();
      return currentYear;
    }
  },
  computed: {
    getMyAge() {
      const currentYear = new Date().getFullYear();
      const myBirthYear = this.myBirthYear;
      let theYear = currentYear - myBirthYear;
      return theYear;
    },
    getAddressData() {
      let { city, province, country } = this.address;
      return city + " " + province + " " + country;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
