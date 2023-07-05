<template>
  <div style="width: 300px; margin: 20px auto">
    <div v-if="step === 1">
      <h1>DISC PERSONALITY</h1>

      <label>Nama Lengkap</label><br />
      <input class="w-full form-control" type="text" v-model="biodata.nama" />
      <br />
      <label>Hobby</label><br />
      <input class="w-full form-control" type="text" v-model="biodata.hobby" />

      <button
        @click="step = 2"
        style="width: 100%; padding: 5px; font-size: 22px; border: none"
      >
        Lanjut
      </button>
    </div>

    <div v-if="step === 2">
      <div v-for="(soal, i) in soals" :key="i">
        <h3>{{ i + 1 }}.</h3>
        <ul style="list-style-type: none; padding: 0; margin: 0">
          <li v-for="(pilih, j) in soal.pilihan" :key="j">
            <label
              ><input type="radio" :value="pilih.type" v-model="soal.jawaban" />
              {{ pilih.text }}</label
            >
          </li>
        </ul>
      </div>

      <br />

      <button
        @click="step = 3"
        style="
          width: 100%;
          padding: 5px;
          font-size: 22px;
          border: none;
          margin-bottom: 100px;
        "
      >
        Lihat Hasil
      </button>
    </div>

    <div
      v-if="step === 3"
      style="text-align: center; width: 300px; margin: 10px auto"
    >
      <h2>Hai {{ biodata.nama }}, Hasil kamu adalah :</h2>
      <h1>{{ typeMost.join(", ") }}</h1>
      <span style="font-weight: 800">{{ result }}</span>

      <p>Lihat penjelasan dengan menekan tombol dibawah</p>

      <a
        href="https://psikologibali.com/tes-disc/"
        target="_blank"
        class="btn btn-yellow"
        >Lihat penjelasan</a
      >
    </div>
  </div>
</template>

<script>
export default {
  name: "Disc",
  computed: {
    result() {
      const variableMapping = {
        D: "Dominance",
        I: "Influence",
        S: "Steadiness",
        C: "Compliance",
      };

      const output = this.typeMost
        .map((variable) => variableMapping[variable])
        .join(", ");

      return output;
    },
    typeMost() {
      let D = 0;
      let I = 0;
      let S = 0;
      let C = 0;

      this.soals.forEach((soal) => {
        if (soal.jawaban === "D") {
          D++;
        }
        if (soal.jawaban === "I") {
          I++;
        }
        if (soal.jawaban === "S") {
          S++;
        }
        if (soal.jawaban === "C") {
          C++;
        }
      });

      let maxVariable = [];
      let maxValue = 0;

      if (D >= maxValue) {
        if (D > maxValue) {
          maxVariable = [];
          maxValue = D;
        }
        maxVariable.push("D");
      }

      if (I >= maxValue) {
        if (I > maxValue) {
          maxVariable = [];
          maxValue = I;
        }
        maxVariable.push("I");
      }

      if (S >= maxValue) {
        if (S > maxValue) {
          maxVariable = [];
          maxValue = S;
        }
        maxVariable.push("S");
      }

      if (C >= maxValue) {
        if (C > maxValue) {
          maxVariable = [];
          maxValue = C;
        }
        maxVariable.push("C");
      }

      return maxVariable;
    },
  },
  methods: {
    handleChangeJawaban() {},
  },
  data() {
    return {
      step: 1,
      biodata: {
        nama: "",
        hobby: "",
      },
      soals: [
        {
          jawaban: "",
          pilihan: [
            {
              text: "Memberi Semangat",
              type: "I",
            },
            {
              text: "Suka Tantangan",
              type: "D",
            },
            {
              text: "Teliti",
              type: "C",
            },
            {
              text: "Suka yg pasti & nyaman",
              type: "S",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Berpendirian teguh",
              type: "C",
            },
            {
              text: "Suka bercerita",
              type: "I",
            },
            {
              text: "Suka memimpin",
              type: "D",
            },
            {
              text: "Suka kedamaian",
              type: "S",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Mau mengalah",
              type: "S",
            },
            {
              text: "Suka berkorban",
              type: "C",
            },
            {
              text: "Pandai bergaul",
              type: "I",
            },
            {
              text: "Berkemauan kuat",
              type: "D",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Penuh pertimbangan",
              type: "C",
            },
            {
              text: "Senang dibimbing",
              type: "S",
            },
            {
              text: "Suka bersaing",
              type: "D",
            },
            {
              text: "Suka meyakinkan",
              type: "I",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Periang",
              type: "I",
            },
            {
              text: "Dihormati orang lain",
              type: "C",
            },
            {
              text: "Cenderung menahan diri",
              type: "S",
            },
            {
              text: "Senang memecahkan masalah",
              type: "D",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Berani",
              type: "D",
            },
            {
              text: "Spontan",
              type: "I",
            },
            {
              text: "Berhati-hati",
              type: "S",
            },
            {
              text: "Terperinci",
              type: "C",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Riang Gembira",
              type: "I",
            },
            {
              text: "Tidak mudah berubah",
              type: "C",
            },
            {
              text: "Santun",
              type: "S",
            },
            {
              text: "Berani mengambil resiko",
              type: "D",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Idealis",
              type: "C",
            },
            {
              text: "Mandiri",
              type: "D",
            },
            {
              text: "Ikut ide teman",
              type: "S",
            },
            {
              text: "Banyak ide / inspirasi",
              type: "I",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Lincah/suka bergaul",
              type: "I",
            },
            {
              text: "Mampu memutuskan",
              type: "D",
            },
            {
              text: "Cinta keluarga",
              type: "S",
            },
            {
              text: "Tekun ulet",
              type: "C",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Perantara/penengah",
              type: "S",
            },
            {
              text: "Suka Privacy",
              type: "C",
            },
            {
              text: "Cepat bertindak",
              type: "D",
            },
            {
              text: "Mudah bergaul",
              type: "I",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Senang berfikir",
              type: "C",
            },
            {
              text: "Suka ngotot, kuat bertahan",
              type: "D",
            },
            {
              text: "Senang bicara & tampil",
              type: "I",
            },
            {
              text: "Bersikap mengalah daripada konflik",
              type: "S",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Pasif dan pengikut",
              type: "S",
            },
            {
              text: "Tak gampang berubah",
              type: "C",
            },
            {
              text: "Senang memerintah",
              type: "D",
            },
            {
              text: "Tidak bisa diam & aktif",
              type: "I",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Mudah menerima saran",
              type: "S",
            },
            {
              text: "Suka memimpin",
              type: "D",
            },
            {
              text: "Berfikir terperinci",
              type: "C",
            },
            {
              text: "Lucu, heboh & humoris",
              type: "I",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Perfeksionis/ingin segalanya sempurna",
              type: "C",
            },
            {
              text: "Suka mengalah",
              type: "S",
            },
            {
              text: "Ambisius",
              type: "D",
            },
            {
              text: "Jadi pusat perhatian",
              type: "I",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Bersemangat/gembira",
              type: "I",
            },
            {
              text: "Berani ambil resiko",
              type: "D",
            },
            {
              text: "Tenang & kalem",
              type: "S",
            },
            {
              text: "Berpendirian tetap",
              type: "C",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Bicara meriah/ramai",
              type: "I",
            },
            {
              text: "Bersikap seperti boss (bossy)",
              type: "D",
            },
            {
              text: "Malu - malu / sungkan",
              type: "S",
            },
            {
              text: "Tanpa ekspresi / datar",
              type: "C",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Mudah berubah & moody",
              type: "I",
            },
            {
              text: "Suka memaksa",
              type: "D",
            },
            {
              text: "Kurang antusias / cuek",
              type: "C",
            },
            {
              text: "Tidak mudah memaafkan",
              type: "S",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Pendiam",
              type: "S",
            },
            {
              text: "Gampang tersinggung",
              type: "C",
            },
            {
              text: "Suka melawan / membantah",
              type: "D",
            },
            {
              text: "Suka cari perhatian",
              type: "I",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Rewel / ngomel yang tidak perlu",
              type: "C",
            },
            {
              text: "Suka takut / khawatir",
              type: "S",
            },
            {
              text: "Pelupa",
              type: "I",
            },
            {
              text: "Cenderung blak-blakkan",
              type: "D",
            },
          ],
        },
        {
          jawaban: "",
          pilihan: [
            {
              text: "Tidak sabaran",
              type: "D",
            },
            {
              text: "Tidak berani memutuskan",
              type: "C",
            },
            {
              text: "Sering ragu-ragu",
              type: "S",
            },
            {
              text: "Suka menyela/ memotong pembicaraan orang lain",
              type: "I",
            },
          ],
        },
      ],
    };
  },
};
</script>