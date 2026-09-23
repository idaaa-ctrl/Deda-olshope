<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Toko Kita - Platform Jual Beli</title>
    <!-- Memuat Tailwind CSS melalui CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome untuk Ikon -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
</head>
<body class="bg-gray-50 min-h-screen font-sans text-gray-800">

    <!-- ================= VIEW: LOGIN ================= -->
    <div id="loginView" class="flex items-center justify-center min-h-screen p-4">
        <div class="bg-white p-8 rounded-2xl shadow-xl w-full max-w-md transition-all duration-300 border border-gray-100">
            <div class="text-center mb-8">
                <div class="inline-flex items-center justify-center w-12 h-12 bg-blue-100 text-blue-600 rounded-full mb-4">
                    <i class="fa-solid fa-store text-xl"></i>
                </div>
                <h2 class="text-3xl font-extrabold text-gray-900">Selamat Datang</h2>
                <p class="text-gray-500 mt-2">Silakan login untuk mulai berbelanja</p>
            </div>
            
            <form onsubmit="prosesLogin(event)">
                <div class="mb-5">
                    <label class="block text-gray-700 text-sm font-bold mb-2" for="loginEmail">Email</label>
                    <input class="w-full px-4 py-3 rounded-lg bg-gray-50 border border-gray-200 focus:border-blue-500 focus:bg-white focus:ring-2 focus:ring-blue-200 outline-none transition-colors" id="loginEmail" type="email" placeholder="contoh@email.com" required>
                </div>
                <div class="mb-6">
                    <label class="block text-gray-700 text-sm font-bold mb-2" for="loginPassword">Password</label>
                    <input class="w-full px-4 py-3 rounded-lg bg-gray-50 border border-gray-200 focus:border-blue-500 focus:bg-white focus:ring-2 focus:ring-blue-200 outline-none transition-colors" id="loginPassword" type="password" placeholder="********" required>
                </div>
                <button class="w-full bg-blue-600 hover:bg-blue-700 text-white font-bold py-3 px-4 rounded-lg transition duration-200 shadow-lg shadow-blue-500/30" type="submit">
                    Masuk ke Toko
                </button>
                <p class="text-center text-sm text-gray-600 mt-6">
                    Belum punya akun? 
                    <button type="button" onclick="ubahView('registerView')" class="text-blue-600 hover:text-blue-800 font-bold focus:outline-none">
                        Daftar di sini
                    </button>
                </p>
            </form>
        </div>
    </div>

    <!-- ================= VIEW: DAFTAR ================= -->
    <div id="registerView" class="hidden flex items-center justify-center min-h-screen p-4">
        <div class="bg-white p-8 rounded-2xl shadow-xl w-full max-w-md transition-all duration-300 border border-gray-100">
            <div class="text-center mb-8">
                <div class="inline-flex items-center justify-center w-12 h-12 bg-green-100 text-green-600 rounded-full mb-4">
                    <i class="fa-solid fa-user-plus text-xl"></i>
                </div>
                <h2 class="text-3xl font-extrabold text-gray-900">Buat Akun</h2>
                <p class="text-gray-500 mt-2">Lengkapi data Anda di bawah ini</p>
            </div>
            
            <form onsubmit="prosesDaftar(event)">
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2" for="regNama">Nama Lengkap</label>
                    <input class="w-full px-4 py-3 rounded-lg bg-gray-50 border border-gray-200 focus:border-green-500 focus:bg-white focus:ring-2 focus:ring-green-200 outline-none transition-colors" id="regNama" type="text" placeholder="Nama Anda" required>
                </div>
                <div class="mb-4">
                    <label class="block text-gray-700 text-sm font-bold mb-2" for="regEmail">Email</label>
                    <input class="w-full px-4 py-3 rounded-lg bg-gray-50 border border-gray-200 focus:border-green-500 focus:bg-white focus:ring-2 focus:ring-green-200 outline-none transition-colors" id="regEmail" type="email" placeholder="contoh@email.com" required>
                </div>
                <div class="mb-6">
                    <label class="block text-gray-700 text-sm font-bold mb-2" for="regPassword">Password</label>
                    <input class="w-full px-4 py-3 rounded-lg bg-gray-50 border border-gray-200 focus:border-green-500 focus:bg-white focus:ring-2 focus:ring-green-200 outline-none transition-colors" id="regPassword" type="password" placeholder="********" required>
                </div>
                <button class="w-full bg-green-600 hover:bg-green-700 text-white font-bold py-3 px-4 rounded-lg transition duration-200 shadow-lg shadow-green-500/30" type="submit">
                    Daftar Sekarang
                </button>
                <p class="text-center text-sm text-gray-600 mt-6">
                    Sudah punya akun? 
                    <button type="button" onclick="ubahView('loginView')" class="text-green-600 hover:text-green-800 font-bold focus:outline-none">
                        Login di sini
                    </button>
                </p>
            </form>
        </div>
    </div>

    <!-- ================= VIEW: KATALOG PRODUK ================= -->
    <div id="catalogView" class="hidden">
        <!-- Navbar Katalog -->
        <nav class="bg-white shadow-sm border-b border-gray-100 sticky top-0 z-50">
            <div class="max-w-7xl mx-auto px-4 py-4 flex flex-wrap justify-between items-center gap-4">
                <h1 class="text-2xl font-extrabold text-blue-600 flex items-center gap-2">
                    <i class="fa-solid fa-store"></i> TokoHub
                </h1>
                
                <div class="flex items-center gap-4">
                    <!-- Tombol Keranjang -->
                    <button class="flex items-center gap-2 bg-blue-50 text-blue-600 px-4 py-2 rounded-xl font-bold hover:bg-blue-100 transition">
                        <i class="fa-solid fa-cart-shopping"></i>
                        <span class="hidden sm:inline">Keranjang</span>
                        <span id="cartCount" class="bg-red-500 text-white text-xs px-2 py-1 rounded-full">0</span>
                    </button>
                    <!-- Tombol Logout -->
                    <button onclick="prosesLogout()" class="flex items-center gap-2 text-gray-500 hover:text-red-500 font-semibold px-2 py-2 transition">
                        <i class="fa-solid fa-arrow-right-from-bracket"></i>
                        <span class="hidden sm:inline">Keluar</span>
                    </button>
                </div>
            </div>
        </nav>

        <main class="max-w-7xl mx-auto px-4 py-8">
            <!-- Header & Filter -->
            <div class="flex flex-col md:flex-row md:items-end justify-between gap-4 mb-8 bg-white p-6 rounded-2xl shadow-sm border border-gray-100">
                <div>
                    <h2 class="text-2xl sm:text-3xl font-extrabold text-gray-800">Katalog Produk</h2>
                    <p class="text-gray-500 text-sm mt-2">Menampilkan total <span id="totalProdukInfo" class="font-bold text-blue-600">0</span> barang tersedia</p>
                </div>

                <div class="flex flex-col sm:flex-row gap-3 w-full md:w-auto">
                    <div class="relative w-full md:w-64">
                        <i class="fa-solid fa-magnifying-glass absolute left-4 top-3.5 text-gray-400"></i>
                        <input type="text" id="searchInput" onkeyup="resetDanFilter()" placeholder="Cari barang..." class="pl-10 pr-4 py-3 w-full bg-gray-50 border border-gray-200 rounded-xl focus:ring-2 focus:ring-blue-500 outline-none transition">
                    </div>
                    <select id="categorySelect" onchange="resetDanFilter()" class="px-4 py-3 bg-gray-50 border border-gray-200 rounded-xl focus:ring-2 focus:ring-blue-500 outline-none w-full sm:w-48 transition cursor-pointer">
                        <option value="Semua">Semua Kategori</option>
                        <option value="Fashion">Fashion</option>
                        <option value="Elektronik">Elektronik</option>
                        <option value="Aksesoris">Aksesoris</option>
                        <option value="Gaya Hidup">Gaya Hidup</option>
                    </select>
                </div>
            </div>

            <!-- Grid Produk -->
            <div id="productGrid" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6"></div>

            <!-- Pesan Kosong (Tidak Ditemukan) -->
            <div id="noProductMessage" class="hidden text-center py-16 text-gray-500 bg-white rounded-2xl border border-gray-100">
                <i class="fa-solid fa-box-open text-6xl mb-4 text-gray-300"></i>
                <p class="text-xl font-bold text-gray-700">Barang tidak ditemukan</p>
                <p class="text-sm mt-1">Coba gunakan kata kunci atau kategori lain.</p>
            </div>

            <!-- Paginasi -->
            <div class="flex justify-center items-center gap-3 mt-12 mb-8" id="paginationContainer">
                <button onclick="gantiHalaman(-1)" id="btnPrev" class="px-5 py-2.5 font-bold border border-gray-200 rounded-xl bg-white hover:bg-gray-50 hover:text-blue-600 transition disabled:opacity-50 disabled:cursor-not-allowed flex items-center gap-2 shadow-sm">
                    <i class="fa-solid fa-chevron-left"></i> <span class="hidden sm:inline">Sebelumnya</span>
                </button>
                <div class="px-4 py-2.5 bg-white border border-gray-200 rounded-xl shadow-sm">
                    <span id="pageInfo" class="text-sm font-bold text-gray-700">1 / 1</span>
                </div>
                <button onclick="gantiHalaman(1)" id="btnNext" class="px-5 py-2.5 font-bold border border-gray-200 rounded-xl bg-white hover:bg-gray-50 hover:text-blue-600 transition disabled:opacity-50 disabled:cursor-not-allowed flex items-center gap-2 shadow-sm">
                    <span class="hidden sm:inline">Selanjutnya</span> <i class="fa-solid fa-chevron-right"></i>
                </button>
            </div>
        </main>
    </div>

    <!-- ================= SCRIPT LOGIKA ================= -->
    <script>
        // --- 1. NAVIGASI VIEW SPA (Single Page Application) ---
        function ubahView(viewId) {
            document.getElementById('loginView').classList.add('hidden');
            document.getElementById('registerView').classList.add('hidden');
            document.getElementById('catalogView').classList.add('hidden');
            
            document.getElementById(viewId).classList.remove('hidden');
            document.getElementById(viewId).classList.add('flex'); // Pastikan flex kembali untuk form
            
            if(viewId === 'catalogView') {
                document.getElementById('catalogView').classList.remove('flex'); // Catalog bukan flex center
                resetDanFilter(); // Muat data barang saat masuk katalog
            }
        }

        function prosesLogin(e) {
            e.preventDefault();
            // Simulasi sukses login
            ubahView('catalogView');
            alert('Berhasil masuk! Selamat berbelanja.');
        }

        function prosesDaftar(e) {
            e.preventDefault();
            // Simulasi sukses daftar
            ubahView('catalogView');
            alert('Akun berhasil dibuat! Selamat datang di TokoHub.');
        }

        function prosesLogout() {
            if(confirm('Apakah Anda yakin ingin keluar?')) {
                ubahView('loginView');
            }
        }


        // --- 2. LOGIKA PRODUK & PAGINASI ---
        // Generate Dummy Data 120 Barang
        const dataProduk = [];
        const daftarKategori = ["Fashion", "Elektronik", "Aksesoris", "Gaya Hidup"];
        const daftarGambar = [
            "https://images.unsplash.com/photo-1523275335684-37898b6baf30?w=400&q=80", // Jam
            "https://images.unsplash.com/photo-1505740420928-5e560c06d30e?w=400&q=80", // Headphone
            "https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=400&q=80", // Sepatu
            "https://images.unsplash.com/photo-1546868871-7041f2a55e12?w=400&q=80"  // Smartwatch
        ];
        
        for (let i = 1; i <= 120; i++) {
            const kat = daftarKategori[i % daftarKategori.length];
            const img = daftarGambar[i % daftarGambar.length];
            dataProduk.push({
                id: i,
                nama: `Produk Premium #${i}`,
                kategori: kat,
                harga: (Math.floor(Math.random() * 40) + 5) * 10000,
                gambar: img,
                stok: Math.floor(Math.random() * 50) + 1
            });
        }

        let halamanSaatIni = 1;
        const jumlahPerHalaman = 12; // 12 item per halaman agar rapi di grid
        let produkTersaring = [...dataProduk];
        let jumlahKeranjang = 0;

        function formatRupiah(angka) {
            return new Intl.NumberFormat('id-ID', { style: 'currency', currency: 'IDR', maximumFractionDigits: 0 }).format(angka);
        }

        function muatHalaman() {
            const grid = document.getElementById('productGrid');
            const noMsg = document.getElementById('noProductMessage');
            grid.innerHTML = '';

            const totalHalaman = Math.ceil(produkTersaring.length / jumlahPerHalaman) || 1;
            
            if (produkTersaring.length === 0) {
                noMsg.classList.remove('hidden');
                document.getElementById('paginationContainer').classList.add('hidden');
                document.getElementById('totalProdukInfo').innerText = 0;
                return;
            } else {
                noMsg.classList.add('hidden');
                document.getElementById('paginationContainer').classList.remove('hidden');
            }

            const indeksMulai = (halamanSaatIni - 1) * jumlahPerHalaman;
            const indeksSelesai = indeksMulai + jumlahPerHalaman;
            const itemTampil = produkTersaring.slice(indeksMulai, indeksSelesai);

            itemTampil.forEach(item => {
                grid.innerHTML += `
                    <div class="bg-white rounded-2xl shadow-sm hover:shadow-xl transition-shadow duration-300 overflow-hidden border border-gray-100 flex flex-col group">
                        <div class="h-48 w-full overflow-hidden relative bg-gray-100">
                            <img src="${item.gambar}" alt="${item.nama}" class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500">
                            <span class="absolute top-3 right-3 bg-white/95 backdrop-blur text-[10px] font-bold text-gray-800 px-2.5 py-1 rounded-full shadow-sm">
                                ${item.kategori}
                            </span>
                        </div>
                        <div class="p-5 flex-1 flex flex-col justify-between">
                            <div>
                                <h3 class="font-bold text-gray-900 text-lg mb-1 line-clamp-1">${item.nama}</h3>
                                <p class="text-xs text-gray-400 font-medium mb-3">Tersisa: ${item.stok} stok</p>
                                <p class="text-xl font-black text-blue-600">${formatRupiah(item.harga)}</p>
                            </div>
                            <button onclick="tambahKeKeranjang()" class="w-full mt-4 bg-gray-50 text-blue-600 hover:bg-blue-600 hover:text-white font-bold py-2.5 rounded-xl transition duration-200 text-sm flex items-center justify-center gap-2">
                                <i class="fa-solid fa-plus"></i> Tambah
                            </button>
                        </div>
                    </div>
                `;
            });

            document.getElementById('pageInfo').innerText = `${halamanSaatIni} / ${totalHalaman}`;
            document.getElementById('btnPrev').disabled = halamanSaatIni === 1;
            document.getElementById('btnNext').disabled = halamanSaatIni === totalHalaman;
            document.getElementById('totalProdukInfo').innerText = produkTersaring.length;
        }

        function resetDanFilter() {
            const keyword = document.getElementById('searchInput').value.toLowerCase();
            const kategori = document.getElementById('categorySelect').value;

            produkTersaring = dataProduk.filter(item => {
                const cocokNama = item.nama.toLowerCase().includes(keyword);
                const cocokKategori = (kategori === "Semua") || (item.kategori === kategori);
                return cocokNama && cocokKategori;
            });

            halamanSaatIni = 1; 
            muatHalaman();
        }

        function gantiHalaman(arah) {
            halamanSaatIni += arah;
            muatHalaman();
            // Scroll otomatis ke bagian atas katalog saat ganti halaman
            window.scrollTo({ top: document.getElementById('catalogView').offsetTop, behavior: 'smooth' }); 
        }

        function tambahKeKeranjang() {
            jumlahKeranjang++;
            const cartBadge = document.getElementById('cartCount');
            cartBadge.innerText = jumlahKeranjang;
            
            // Animasi kecil pada tombol keranjang
            cartBadge.classList.add('scale-125');
            setTimeout(() => {
                cartBadge.classList.remove('scale-125');
            }, 200);
        }
    </script>
</body>
</html>