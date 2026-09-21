<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>WIRATIKA - Pusat Digital Ambalan</title>
    <style>
        *{margin:0;padding:0;box-sizing:border-box;font-family:'Segoe UI',Roboto,sans-serif;}
        :root{
            --coklat:#795548;--hijau:#2E7D32;--krem:#F5F5DC;--putih:#FFF;--abu:#757575;
            --latar:#FAFAFA;--benar:#2E7D32;--salah:#C62828;--peringatan:#FF9800;
            --bayangan:0 3px 10px rgba(0,0,0,0.08);
        }
        body{background:var(--latar);color:#212;margin:0 auto;max-width:480px;padding-bottom:90px;}

        /* === HEADER & ROLE === */
        .header{background:linear-gradient(135deg,var(--coklat),var(--hijau));color:var(--putih);padding:1.5rem;border-radius:0 0 20px;box-shadow:var(--bayangan);}
        .role-pilih{display:flex;gap:0.5rem;margin-top:0.8rem;}
        .role-btn{flex:1;padding:0.6rem;border:2px solid rgba(255,255,255,0.5);background:transparent;color:var(--putih);border-radius:8px;cursor:pointer;}
        .role-btn.aktif{background:var(--putih);color:var(--coklat);font-weight:600;}
        .slogan{margin-top:0.8rem;text-align:center;font-style:italic;opacity:0.9;}

        /* === KONTAINER & HALAMAN === */
        .isi{padding:1.2rem;}
        .halaman{display:none;}.halaman.aktif{display:block;}
        .kartu{background:var(--putih);border-radius:14px;padding:1.3rem;margin-bottom:1rem;box-shadow:var(--bayangan);}
        .kartu h2{color:var(--coklat);font-size:1.2rem;margin-bottom:0.8rem;display:flex;align-items:center;gap:0.5rem;}
        .kartu h3{font-size:1.05rem;color:var(--hijau);margin:1rem 0 0.5rem;}
        .kartu p,.kartu li{color:var(--abu);line-height:1.6;}
        .kartu ul{margin-left:1.4rem;}
        .admin-saja{display:none;}.admin .admin-saja{display:block;}

        /* === BAGIAN TEKNIS DAN GAMBAR === */
        .ilustrasi{width:100%;aspect-ratio:16/9;background:#E0E0E0;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:2.5rem;color:#999;margin:0.8rem 0;}
        .langkah{background:rgba(121,85,72,0.05);border-radius:8px;padding:0.8rem;margin:0.5rem 0;}
        .langkah b{color:var(--coklat);}

        /* === FORM & TOMBOL === */
        input, select, textarea, button{width:100%;padding:0.9rem;border:1px solid #DDD;border-radius:10px;font-size:1rem;margin:0.4rem 0;}
        .tombol{border:none;cursor:pointer;transition:0.2rem;font-weight:600;}
        .tombol-utama{background:linear-gradient(90deg,var(--coklat),var(--hijau));color:var(--putih);}
        .tombol-kedua{background:transparent;color:var(--coklat);border:2px solid var(--coklat);}
        .tombol-mini{width:auto;padding:0.5rem 0.8rem;font-size:0.9rem;margin-right:0.5rem;}
        .form-edit{display:none;}.sedang-edit .form-edit{display:block;}
        .sedang-edit .baca-saja{display:none;}

        /* === ABSEN & DAFTAR === */
        .daftar-nama{max-height:200px;overflow-y:auto;}
        .item-absen{display:flex;justify-content:space-between;align-items:center;padding:0.7rem;border-bottom:1px solid #EEE;}
        .status-hadir{color:var(--benar);font-weight:600;}
        .status-izin{color:var(--peringatan);font-weight:600;}
        .status-sakit{color:#1976D2;font-weight:600;}
        .status-alpha{color:var(--salah);font-weight:600;}

        /* === PROGRESS & MENU === */
        .progress{margin:0.5rem 0;}
        .bar{width:100%;height:10px;background:#EEE;border-radius:5px;overflow:hidden;}
        .isi-bar{height:100%;background:linear-gradient(90deg,var(--coklat),var(--hijau));}
        .grid{display:grid;grid-template-columns:repeat(2,1fr);gap:0.8rem;}
        .item-grid{padding:1rem;background:var(--putih);border-radius:12px;text-align:center;cursor:pointer;box-shadow:var(--bayangan);transition:0.2s;}
        .item-grid:hover{transform:translateY(-2px);background:var(--krem);}
        .ikon{font-size:1.8rem;margin-bottom:0.5rem;}

        /* === NAVIGASI BAWAH === */
        .nav{position:fixed;bottom:0;left:50%;transform:translateX(-50%);width:100%;max-width:480px;background:var(--putih);display:flex;justify-content:space-around;padding:0.8rem 0;box-shadow:0 -3px 10px rgba(0,0,0,0.08);border-radius:16px 16px 0 0;}
        .nav-btn{display:flex;flex-direction:column;align-items:center;gap:0.2rem;color:var(--abu);cursor:pointer;}
        .nav-btn.aktif{color:var(--coklat);font-weight:600;}
    </style>
</head>
<body>

<!-- HEADER -->
<div class="header">
    <h1>🏕️ WIRATIKA</h1>
    <p>Pusat Digital Ambalan</p>
    <div class="role-pilih">
        <button class="role-btn aktif" onclick="gantiRole('anggota')">Anggota</button>
        <button class="role-btn" onclick="gantiRole('admin')">Admin</button>
    </div>
    <div class="slogan">"Satyaku Kudarmakan, Darmaku Kubaktikan"</div>
</div>

<div class="isi" id="appBody">
    <!-- BERANDA -->
    <div id="halBeranda" class="halaman aktif">
        <div class="kartu">
            <h2>🔔 Pengumuman</h2>
            <div class="baca-saja" id="bacaPengumuman">Latihan rutin minggu ini hari Sabtu 28 Sep pukul 08.00 WIB di Lapangan Sekolah</div>
            <div class="form-edit">
                <textarea id="inputPengumuman">Latihan rutin minggu ini hari Sabtu 28 Sep pukul 08.00 WIB di Lapangan Sekolah</textarea>
                <button class="tombol tombol-utama tombol-mini" onclick="simpanPengumuman()">Simpan</button>
            </div>
            <button class="tombol tombol-kedua tombol-mini admin-saja" onclick="document.querySelector('#halBeranda').classList.toggle('sedang-edit')">Ubah</button>
        </div>

        <div class="grid">
            <div class="item-grid" onclick="buka('ambalan')"><div class="ikon">🏛️</div><span>Profil</span></div>
            <div class="item-grid" onclick="buka('materi')"><div class="ikon">📚</div><span>Materi</span></div>
            <div class="item-grid" onclick="buka('teknis')"><div class="ikon">🛠️</div><span>Teknis</span></div>
            <div class="item-grid" onclick="buka('kegiatan')"><div class="ikon">📅</div><span>Kegiatan</span></div>
            <div class="item-grid" onclick="buka('absensi')"><div class="ikon">✅</div><span>Absensi</span></div>
            <div class="item-grid" onclick="buka('profil')"><div class="ikon">👤</div><span>Profil Saya</span></div>
        </div>
    </div>

    <!-- PROFIL AMBALAN -->
    <div id="halAmbalan" class="halaman">
        <div class="kartu">
            <h2>Profil Ambalan</h2>
            <div class="baca-saja" id="bacaAmbalan">
                <p><b>Nama:</b> Ambalan Sultan Agung</p>
                <p><b>Gudep:</b> 01.001 SMAN 1 Bandung</p>
                <p><b>Berdiri:</b> 1998</p>
                <p><b>Visi:</b> Membentuk anggota beriman, cerdas, dan berbakti</p>
            </div>
            <div class="form-edit">
                <textarea id="inputAmbalan" rows="6">Nama: Ambalan Sultan Agung
Gudep: 01.001 SMAN 1 Bandung
Berdiri: 1998
Visi: Membentuk anggota beriman, cerdas, dan berbakti</textarea>
                <button class="tombol tombol-utama" onclick="simpanAmbalan()">Simpan Perubahan</button>
            </div>
            <button class="tombol tombol-kedua admin-saja" onclick="document.querySelector('#halAmbalan').classList.toggle('sedang-edit')">Ubah Data</button>
        </div>
        <button class="tombol tombol-kedua" onclick="buka('beranda')">← Kembali</button>
    </div>

    <!-- MATERI JELAS & LENGKAP -->
    <div id="halMateri" class="halaman">
        <div class="kartu">
            <h2>📚 Materi Kepramukaan</h2>
            <h3>1. Tri Satya</h3>
            <p>Janji setia yang diucapkan setiap anggota Pramuka:</p>
            <ol>
                <li>Takwa kepada Tuhan Yang Maha Esa</li>
                <li>Cinta alam dan kasih sayang sesama manusia</li>
                <li>Patriot yang sopan dan ksatria</li>
                <li>Patuh dan bergotong royong</li>
                <li>Bertanggung jawab dan berilmu luas</li>
                <li>Berbakti demi nusa bangsa</li>
                <li>Disiplin, terampil, dan sederhana</li>
            </ol>

            <h3>2. Dasa Darma</h3>
            <p>10 ketentuan tingkah laku: Takwa, Cinta Tanah Air, Cinta Alam, Disiplin, Menolong, Tegas, Hemat, Cinta Kerja, Berilmu, Suci.</p>

            <h3>3. Semboyan Penegak</h3>
            <p><b>"Satyaku Kudarmakan, Darmaku Kubaktikan"</b></p>
            <p>Artinya: Apa yang diucapkan sebagai janji pasti dilaksanakan, dan kewajiban yang dipikul dijalankan sepenuhnya sebagai pengabdian.</p>
        </div>
        <button class="tombol tombol-kedua" onclick="buka('beranda')">← Kembali</button>
    </div>

    <!-- TEKNIS DENGAN FOTO & CARA -->
    <div id="halTeknis" class="halaman">
        <div class="kartu">
            <h2>🛠️ Panduan Teknis</h2>

            <h3>Simpul Mati</h3>
            <p><b>Fungsi:</b> Mengikat dua ujung tali sama ukuran agar tidak lepas</p>
            <div class="ilustrasi">🪢 Ilustrasi Simpul Mati</div>
            <div class="langkah">
                <p><b>Cara membuat:</b></p>
                <p>1. Silangkan tali kiri di atas tali kanan</p>
                <p>2. Putar ujung tali kiri ke bawah membentuk lingkaran</p>
                <p>3. Masukkan ujung tali kanan ke dalam lingkaran</p>
                <p>4. Tarik kedua ujung hingga kencang</p>
            </div>

            <h3>Simpul Pangkal</h3>
            <p><b>Fungsi:</b> Mengikat tali pada tiang/pohon sebagai tumpuan</p>
            <div class="ilustrasi">🪢 Ilustrasi Simpul Pangkal</div>
            <div class="langkah">
                <p><b>Cara membuat:</b></p>
                <p>1. Lilitkan tali satu putaran penuh pada tiang</p>
                <p>2. Lilitkan ujung tali di atas tali utama</p>
                <p>3. Masukkan ke celah lilitan pertama</p>
                <p>4. Tarik hingga kencang</p>
            </div>
        </div>
        <button class="tombol tombol-kedua" onclick="buka('beranda')">← Kembali</button>
    </div>

    <!-- KEGIATAN BISA DIUBAH -->
    <div id="halKegiatan" class="halaman">
        <div class="kartu">
            <h2>📅 Jadwal Kegiatan</h2>
            <div id="daftarKegiatan"></div>
            <div class="admin-saja">
                <h3>Tambah/Ubah Kegiatan</h3>
                <input type="text" id="namaKegiatan" placeholder="Nama Kegiatan">
                <input type="text" id="tglKegiatan" placeholder="Tanggal & Waktu">
                <input type="text" id="lokasiKegiatan" placeholder="Lokasi">
                <button class="tombol tombol-utama" onclick="tambahKegiatan()">Simpan Kegiatan</button>
            </div>
        </div>
        <button class="tombol tombol-kedua" onclick="buka('beranda')">← Kembali</button>
    </div>

    <!-- ABSENSI MANDIRI -->
    <div id="halAbsensi" class="halaman">
        <div class="kartu">
            <h2>✅ Absensi Latihan</h2>
            <input type="text" id="namaAbsen" placeholder="Ketik Nama Lengkap Kamu">
            <select id="statusAbsen">
                <option value="hadir">Hadir</option>
                <option value="izin">Izin</option>
                <option value="sakit">Sakit</option>
            </select>
            <button class="tombol tombol-utama" onclick="kirimAbsen()">Konfirmasi Kehadiran</button>
            <hr style="margin:1rem 0;">
            <h3>Daftar Hadir</h3>
            <div class="daftar-nama" id="riwayatAbsen"></div>
        </div>
        <button class="tombol tombol-kedua" onclick="buka('beranda')">← Kembali</button>
    </div>

    <!-- BIODATA BISA DIISI SENDIRI -->
    <div id="halProfil" class="halaman">
        <div class="kartu">
            <h2>👤 Profil Anggota</h2>
            <input type="text" id="isiNama" placeholder="Nama Lengkap">
            <input type="text" id="isiKelas" placeholder="Kelas">
            <select id="isiTingkat">
                <option value="">Pilih Tingkatan</option>
                <option>Penegak Tamu</option>
                <option>Penegak Bantara</option>
                <option>Penegak Laksana</option>
            </select>
            <button class="tombol tombol-utama" onclick="simpanProfil()">Simpan Data Diri</button>
            <div id="tampilProfil" style="margin-top:1rem;"></div>

            <h3>📊 Perkembangan</h3>
            <div class="progress"><div>SKU Laksana (80%)</div><div class="bar"><div class="isi-bar" style="width:80%"></div></div></div>
            <div class="progress"><div>TKK Umum (60%)</div><div class="bar"><div class="isi-bar" style="width:60%"></div></div></div>
        </div>
        <button class="tombol tombol-kedua" onclick="buka('beranda')">← Kembali</button>
    </div>
</div>

<!-- NAVIGASI -->
<div class="nav">
    <div class="nav-btn aktif" onclick="buka('beranda')"><span>🏠</span><span>Beranda</span></div>
    <div class="nav-btn" onclick="buka('materi')"><span>📚</span><span>Materi</span></div>
    <div class="nav-btn" onclick="buka('kegiatan')"><span>📅</span><span>Kegiatan</span></div>
    <div class="nav-btn" onclick="buka('absensi')"><span>✅</span><span>Absen</span></div>
    <div class="nav-btn" onclick="buka('profil')"><span>👤</span><span>Saya</span></div>
</div>

<script>
// Data Awal & Penyimpanan
let dataKegiatan = JSON.parse(localStorage.getItem('kegiatan')) || [
    {nama:'Latihan Rutin', tgl:'Setiap Sabtu 08.00 WIB', lokasi:'Lapangan Sekolah'},
    {nama:'Pelantikan', tgl:'05 Okt 2026 07.00 WIB', lokasi:'Halaman Sekolah'}
];
let dataAbsen = JSON.parse(localStorage.getItem('absen')) || [];
let profilSaya = JSON.parse(localStorage.getItem('profil')) || {};

// Ganti Peran Tampilan
function gantiRole(tipe){
    document.querySelectorAll('.role-btn').forEach(b=>b.classList.remove('aktif'));
    event.target.classList.add('aktif');
    if(tipe==='admin') document.getElementById('appBody').classList.add('admin');
    else document.getElementById('appBody').classList.remove('admin');
}

// Pindah Halaman
function buka(tujuan){
    document.querySelectorAll('.halaman').forEach(h=>h.classList.remove('aktif'));
    document.querySelectorAll('.nav-btn').forEach(n=>n.classList.remove('aktif'));
    document.getElementById('hal'+tujuan.charAt(0).toUpperCase()+tujuan.slice(1)).classList.add('aktif');
}

// Kelola Kegiatan
function tampilKegiatan(){
    let html='';
    dataKegiatan.forEach((k,i)=>{
        html += `<div style="padding:0.7rem;border-bottom:1px solid #EEE;">
            <p><b>${k.nama}</b></p><p>${k.tgl} | ${k.lokasi}</p>
            <button class="tombol tombol-kedua tombol-mini admin-saja" onclick="hapusKegiatan(${i})">Hapus</button>
        </div>`;
    });
    document.getElementById('daftarKegiatan').innerHTML = html;
}
function tambahKegiatan(){
    dataKegiatan.push({
        nama:document.getElementById('namaKegiatan').value,
        tgl:document.getElementById('tglKegiatan').value,
        lokasi:document.getElementById('lokasiKegiatan').value
    });
    simpanData();tampilKegiatan();
}
function hapusKegiatan(i){
    dataKegiatan.splice(i,1);simpanData();tampilKegiatan();
}

// Absensi Mandiri
function kirimAbsen(){
    let nama = document.getElementById('namaAbsen').value.trim();
    let stt = document.getElementById('statusAbsen').value;
    if(!nama) return alert('Masukkan nama lengkap');
    dataAbsen.push({nama:nama, status:stt, waktu:new Date().toLocaleString()});
    simpanData();tampilAbsen();
    alert('Absen berhasil terkirim!');
    document.getElementById('namaAbsen').value='';
}
function tampilAbsen(){
    let html='';
    dataAbsen.forEach(a=>{
        let kelas = a.status==='hadir'?'status-hadir':a.status==='izin'?'status-izin':'status-sakit';
        html += `<div class="item-absen"><span>${a.nama}</span><span class="${kelas}">${a.status.toUpperCase()}</span></div>`;
    });
    document.getElementById('riwayatAbsen').innerHTML = html;
}

// Profil Anggota
function simpanProfil(){
    profilSaya = {
        nama:document.getElementById('isiNama').value,
        kelas:document.getElementById('isiKelas').value,
        tingkat:document.getElementById('isiTingkat').value
    };
    localStorage.setItem('profil', JSON.stringify(profilSaya));
    tampilProfil();
}
function tampilProfil(){
    if(profilSaya.nama){
        document.getElementById('tampilProfil').innerHTML = `<hr><p><b>Nama:</b> ${profilSaya.nama}</p><p><b>Kelas:</b> ${profilSaya.kelas||'-'}</p><p><b>Tingkatan:</b> ${profilSaya.tingkat||'-'}</p>`;
        document.getElementById('isiNama').value = profilSaya.nama;
        document.getElementById('isiKelas').value = profilSaya.kelas||'';
        document.getElementById('isiTingkat').value = profilSaya.tingkat||'';
    }
}

// Simpan Semua Data
function simpanData(){
    localStorage.setItem('kegiatan', JSON.stringify(dataKegiatan));
    localStorage.setItem('absen', JSON.stringify(dataAbsen));
}
function simpanPengumuman(){
    document.getElementById('bacaPengumuman').textContent = document.getElementById('inputPengumuman').value;
    alert('Pengumuman diperbarui');
}
function simpanAmbalan(){alert('Data Ambalan diperbarui');}

// Muat Awal
tampilKegiatan();tampilAbsen();tampilProfil();
</script>
</body>
</html>

