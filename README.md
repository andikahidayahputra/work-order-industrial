
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Work Order</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

    * { box-sizing: border-box; }

    body {
      font-family: 'Roboto', sans-serif;
      background: linear-gradient(135deg, #43cea2, #185a9d);
      margin: 0;
      padding: 2rem 1rem 4rem;
      min-height: 100vh;
      display: flex;
      justify-content: center;
    }

    .container {
      background: #ffffffee;
      border-radius: 12px;
      box-shadow: 0 8px 25px rgba(0,0,0,0.15);
      width: 100%;
      max-width: 720px;
      padding: 2rem 3rem;
      color: #222;
    }

    h1 {
      margin-top: 0;
      margin-bottom: 1.2rem;
      color: #222;
      font-weight: 700;
      font-size: 2.1rem;
      text-align: center;
    }

    form {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1.5rem 2rem;
      margin-bottom: 2rem;
    }

    form > div { display: flex; flex-direction: column; }

    label {
      font-weight: 600;
      margin-bottom: 0.4rem;
      color: #333;
    }

    input[type="text"],
    input[type="date"],
    input[type="file"],
    select,
    textarea {
      padding: 0.5rem 0.75rem;
      border-radius: 6px;
      border: 1.7px solid #777;
      font-size: 1rem;
      font-family: inherit;
      transition: border-color 0.3s ease;
    }

    input[type="text"]:focus,
    input[type="date"]:focus,
    select:focus,
    textarea:focus {
      outline: none;
      border-color: #43cea2;
      box-shadow: 0 0 10px #43cea266;
    }

    textarea {
      resize: vertical;
      min-height: 70px;
      grid-column: span 2;
    }

    .full-width { grid-column: span 2; }

    button {
      grid-column: span 2;
      background: #43cea2;
      color: white;
      font-weight: 700;
      border: none;
      border-radius: 9px;
      padding: 0.75rem 1rem;
      cursor: pointer;
      font-size: 1.15rem;
      transition: background 0.3s ease;
    }

    button:hover { background: #2aab8c; }

    #listPekerjaanSection {
      background: #fff;
      border-radius: 12px;
      box-shadow: 0 6px 20px rgba(0,0,0,0.12);
      padding: 1.8rem 2.4rem;
      max-height: 420px;
      overflow-y: auto;
    }

    #listPekerjaanSection h2 {
      margin-top: 0;
      border-bottom: 2px solid #43cea2;
      padding-bottom: 0.4rem;
    }

    .pekerjaan-card {
      border: 1px solid #bbb;
      border-radius: 10px;
      padding: 1.1rem 1.4rem;
      margin-bottom: 1rem;
      background: #f5fdfa;
      box-shadow: 0 2px 6px rgba(0,0,0,0.02);
    }

    .pekerjaan-card dl {
      display: grid;
      grid-template-columns: 140px 1fr;
      row-gap: 0.5rem;
      column-gap: 1.2rem;
    }

    .pekerjaan-card dt {
      font-weight: 600;
      color: #33695c;
    }

    .pekerjaan-card dd {
      margin: 0;
      word-wrap: break-word;
    }

    .pekerjaan-card img {
      margin-top: 1rem;
      max-width: 100%;
      border-radius: 8px;
    }

    .btn-clear {
      background: #d9534f;
      padding: 0.6rem 1.1rem;
      border-radius: 7px;
      color: white;
      font-weight: 700;
      cursor: pointer;
      border: none;
      margin-top: 0.5rem;
      transition: background 0.3s ease;
    }

    .btn-clear:hover { background: #b52b27; }

    .delete-button {
      color: red; /* Warna merah untuk tombol hapus */
      font-weight: bold; /* Bold untuk tombol hapus */
      margin-left: 10px; /* Jarak antara tombol edit dan hapus */
    }

    .tgl-selesai {
      color: red; /* Warna merah untuk tanggal selesai */
      font-weight: bold; /* Bold untuk tanggal selesai */
    }

    @media (max-width: 700px) {
      form { grid-template-columns: 1fr; }
      textarea, button { grid-column: 1 / -1; }
    }
  </style>
</head>
<body>
<div class="container">
  <h1>Work Order</h1>
  <form id="pekerjaanForm">
    <div>
      <label for="namaPekerjaan">Nama Pekerjaan</label>
      <input type="text" id="namaPekerjaan" required />
    </div>
    <div>
      <label for="tglMulai">Tanggal Mulai</label>
      <input type="date" id="tglMulai" required />
    </div>
    <div>
      <label for="penanggungJawab">Penanggung Jawab</label>
      <input type="text" id="penanggungJawab" />
    </div>
    <div class="full-width">
      <label for="deskripsiPekerjaan">Deskripsi</label>
      <textarea id="deskripsiPekerjaan" required></textarea>
    </div>
    <div>
      <label for="prioritas">Prioritas</label>
      <select id="prioritas" required>
        <option value="" disabled selected>Pilih</option>
        <option>Rendah</option>
        <option>Sedang</option>
        <option>Tinggi</option>
        <option>Urgent</option>
      </select>
    </div>
    <div>
      <label for="tglSelesai">Tanggal Selesai</label>
      <input type="date" id="tglSelesai" />
    </div>
    <div>
      <label for="status">Status</label>
      <select id="status" required>
        <option value="" disabled selected>Pilih</option>
        <option>Belum Mulai</option>
        <option>Sedang Berjalan</option>
        <option>Selesai</option>
        <option>Ditunda</option>
      </select>
    </div>
    <div class="full-width">
      <label for="gambarPekerjaan">Unggah Gambar (opsional)</label>
      <input type="file" id="gambarPekerjaan" accept="image/*" />
    </div>
    <button type="submit">Simpan Pekerjaan</button>
  </form>

  <section id="listPekerjaanSection" style="display:none;">
    <h2>Daftar Pekerjaan</h2>
    <div id="listPekerjaan"></div>
    <button id="btnClear" class="btn-clear">Hapus Semua</button>
  </section>
</div>

<script>
  let editIndex = -1; // Menyimpan index pekerjaan yang sedang diedit

  function formatDateIndo(dateStr) {
    if (!dateStr) return '-';
    const d = new Date(dateStr);
    if (isNaN(d)) return '-';
    return d.toLocaleDateString('id-ID', {day:'numeric', month:'long', year:'numeric'});
  }

  function loadPekerjaan() {
    const dp = localStorage.getItem('daftarPekerjaan');
    return dp ? JSON.parse(dp) : [];
  }

  function savePekerjaan(data) {
    localStorage.setItem('daftarPekerjaan', JSON.stringify(data));
  }

  function renderPekerjaanList() {
    const list = loadPekerjaan();
    const section = document.getElementById('listPekerjaanSection');
    const container = document.getElementById('listPekerjaan');

    if (list.length === 0) {
      section.style.display = 'none';
      container.innerHTML = '';
      return;
    }

    section.style.display = 'block';
    container.innerHTML = '';

    list.forEach((item, index) => {
      const card = document.createElement('div');
      card.className = 'pekerjaan-card';

      const dl = document.createElement('dl');

      function addRow(label, val, isDate = false) {
        const dt = document.createElement('dt');
        dt.textContent = label;
        const dd = document.createElement('dd');
        dd.textContent = val || '-';
        if (isDate) {
          dd.classList.add('tgl-selesai'); // Tambahkan kelas untuk tanggal selesai
        }
        dl.appendChild(dt);
        dl.appendChild(dd);
      }

      addRow('Nama Pekerjaan:', item.namaPekerjaan);
      addRow('Tanggal Mulai:', formatDateIndo(item.tglMulai));
      addRow('Penanggung Jawab:', item.penanggungJawab);
      addRow('Deskripsi:', item.deskripsiPekerjaan);
      addRow('Prioritas:', item.prioritas);
      addRow('Tanggal Selesai:', formatDateIndo(item.tglSelesai), true); // Tandai sebagai tanggal

      card.appendChild(dl);

      if (item.gambar) {
        const img = document.createElement('img');
        img.src = item.gambar;
        img.alt = 'Gambar Pekerjaan';
        card.appendChild(img);
      }

      // Tambahkan tombol edit
      const editButton = document.createElement('button');
      editButton.textContent = 'Edit';
      editButton.onclick = () => editPekerjaan(index);
      card.appendChild(editButton);

      // Tambahkan tombol hapus
      const deleteButton = document.createElement('button');
      deleteButton.textContent = 'Hapus';
      deleteButton.className = 'delete-button'; // Tambahkan kelas untuk tombol hapus
      deleteButton.onclick = () => deletePekerjaan(index);
      card.appendChild(deleteButton);

      container.appendChild(card);
    });
  }

  function editPekerjaan(index) {
    const list = loadPekerjaan();
    const pekerjaan = list[index];
    editIndex = index; // Simpan index pekerjaan yang sedang diedit

    // Isi form dengan data pekerjaan
    document.getElementById('namaPekerjaan').value = pekerjaan.namaPekerjaan;
    document.getElementById('tglMulai').value = pekerjaan.tglMulai;
    document.getElementById('penanggungJawab').value = pekerjaan.penanggungJawab;
    document.getElementById('deskripsiPekerjaan').value = pekerjaan.deskripsiPekerjaan;
    document.getElementById('prioritas').value = pekerjaan.prioritas;
    document.getElementById('tglSelesai').value = pekerjaan.tglSelesai;
    document.getElementById('status').value = pekerjaan.status;
    // Reset file input
    document.getElementById('gambarPekerjaan').value = '';
  }

  function deletePekerjaan(index) {
    const list = loadPekerjaan();
    list.splice(index, 1); // Hapus pekerjaan dari array
    savePekerjaan(list); // Simpan kembali ke Local Storage
    renderPekerjaanList(); // Render ulang daftar pekerjaan
  }

  document.getElementById('pekerjaanForm').addEventListener('submit', function(e) {
    e.preventDefault();
    const form = e.target;
    const fileInput = document.getElementById('gambarPekerjaan');
    const file = fileInput.files[0];

    const pekerjaan = {
      namaPekerjaan: form.namaPekerjaan.value.trim(),
      tglMulai: form.tglMulai.value,
      penanggungJawab: form.penanggungJawab.value.trim(),
      deskripsiPekerjaan: form.deskripsiPekerjaan.value.trim(),
      prioritas: form.prioritas.value,
      tglSelesai: form.tglSelesai.value,
      status: form.status.value,
      gambar: null
    };

    if (!pekerjaan.namaPekerjaan || !pekerjaan.tglMulai || !pekerjaan.deskripsiPekerjaan || !pekerjaan.prioritas || !pekerjaan.status) {
      alert('Mohon lengkapi semua bidang wajib.');
      return;
    }

    function simpanDanRender() {
      const list = loadPekerjaan();
      if (editIndex === -1) {
        list.push(pekerjaan); // Tambah pekerjaan baru
      } else {
        list[editIndex] = pekerjaan; // Update pekerjaan yang ada
        editIndex = -1; // Reset editIndex setelah update
      }
      savePekerjaan(list);
      alert('Pekerjaan disimpan. Data pekerjaan akan tetap ada setelah disimpan.');
      form.reset();
      form.prioritas.selectedIndex = 0;
      form.status.selectedIndex = 0;
      renderPekerjaanList();
    }

    if (file) {
      const reader = new FileReader();
      reader.onload = function(e) {
        pekerjaan.gambar = e.target.result;
        simpanDanRender();
      };
      reader.readAsDataURL(file);
    } else {
      simpanDanRender();
    }
  });

  document.getElementById('btnClear').addEventListener('click', () => {
    if (confirm('Hapus semua pekerjaan?')) {
      localStorage.removeItem('daftarPekerjaan');
      renderPekerjaanList();
    }
  });

  window.addEventListener('DOMContentLoaded', renderPekerjaanList);
</script>
</body>
</html>
