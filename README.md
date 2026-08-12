<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Khidmah Media Store - Sistem Presensi</title>
  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- FontAwesome Icons -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <!-- Google Fonts (Poppins) -->
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
  
  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            poppins: ['Poppins', 'sans-serif'],
          },
          colors: {
            goldPrimary: '#D4AF37',
            goldLight: '#F3E5AB',
            darkBg: '#0F172A',
          }
        }
      }
    }
  </script>

  <style>
    body {
      font-family: 'Poppins', sans-serif;
      background: radial-gradient(circle at top, #1e293b, #0f172a, #090d16);
    }
    .glass-card {
      background: rgba(30, 41, 59, 0.7);
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);
      border: 1px solid rgba(212, 175, 55, 0.2);
    }
    .gold-gradient-text {
      background: linear-gradient(135deg, #FFF6D5 0%, #D4AF37 50%, #AA7C11 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    .gold-button {
      background: linear-gradient(135deg, #D4AF37 0%, #AA7C11 100%);
      box-shadow: 0 4px 20px rgba(212, 175, 55, 0.3);
    }
    .gold-button:hover {
      background: linear-gradient(135deg, #E5C158 0%, #C5931D 100%);
      box-shadow: 0 6px 25px rgba(212, 175, 55, 0.5);
    }
    .logo-glow {
      filter: drop-shadow(0 0 15px rgba(212, 175, 55, 0.3));
    }
  </style>
</head>
<body class="text-slate-100 min-h-screen flex items-center justify-center p-4 selection:bg-yellow-500 selection:text-black">

  <!-- MAIN CONTAINER -->
  <main class="w-full max-w-md my-auto">

    <!-- LOGIN CARD -->
    <div class="glass-card rounded-3xl p-8 shadow-2xl space-y-6 relative overflow-hidden">
      
      <!-- Hiasan Cahaya Latar Belakang -->
      <div class="absolute -top-20 -left-20 w-40 h-40 bg-yellow-500/10 rounded-full blur-3xl pointer-events-none"></div>
      <div class="absolute -bottom-20 -right-20 w-40 h-40 bg-amber-600/10 rounded-full blur-3xl pointer-events-none"></div>

      <!-- HEADER LOGO & JUDUL -->
      <div class="text-center space-y-3">
        <div class="w-28 h-28 mx-auto flex items-center justify-center transition-transform hover:scale-105 duration-300">
          <img 
            src="https://lh3.googleusercontent.com/d/14X6YZs3II1C1B96O6JXY37AmqHt1aS6X" 
            alt="Logo Khidmah Media Store" 
            class="w-full h-full object-contain logo-glow"
          >
        </div>
        <div>
          <h1 class="text-2xl font-extrabold tracking-wider gold-gradient-text uppercase">KHIDMAH MEDIA STORE</h1>
          <p class="text-xs text-slate-400 font-medium tracking-wide mt-1">Sistem Presensi Online Enterprise</p>
        </div>
      </div>

      <!-- FORM LOGIN -->
      <form id="formLogin" onsubmit="handleLogin(event)" class="space-y-4 pt-2">
        
        <!-- Input Username -->
        <div>
          <label class="block text-xs font-medium text-slate-300 mb-1.5 flex items-center gap-2">
            <i class="fa-solid fa-user text-amber-400/80"></i> Username / Email
          </label>
          <div class="relative">
            <input 
              type="text" 
              id="loginUser" 
              required 
              placeholder="Masukkan username Anda"
              class="w-full bg-slate-900/60 border border-slate-700/80 rounded-xl px-4 py-3.5 text-xs text-white placeholder-slate-500 focus:outline-none focus:border-amber-400 focus:ring-1 focus:ring-amber-400 transition"
            >
          </div>
        </div>

        <!-- Input Password -->
        <div>
          <label class="block text-xs font-medium text-slate-300 mb-1.5 flex items-center gap-2">
            <i class="fa-solid fa-key text-amber-400/80"></i> Password
          </label>
          <div class="relative">
            <input 
              type="password" 
              id="loginPass" 
              required 
              placeholder="••••••••"
              class="w-full bg-slate-900/60 border border-slate-700/80 rounded-xl px-4 py-3.5 text-xs text-white placeholder-slate-500 focus:outline-none focus:border-amber-400 focus:ring-1 focus:ring-amber-400 transition"
            >
          </div>
        </div>

        <!-- Tombol Login -->
        <button 
          type="submit" 
          id="btnLogin" 
          class="w-full gold-button text-slate-950 font-bold py-3.5 rounded-xl text-xs uppercase tracking-wider transition-all duration-300 flex items-center justify-center gap-2 mt-6 active:scale-95"
        >
          <i class="fa-solid fa-right-to-bracket"></i>
          <span>MASUK APLIKASI</span>
        </button>
      </form>

      <!-- FOOTER / KETERANGAN -->
      <div class="text-center pt-2 border-t border-slate-700/40">
        <p class="text-[10px] text-slate-500">© 2026 Khidmah Media Store. All Rights Reserved.</p>
      </div>

    </div>

  </main>

  <!-- JAVASCRIPT KONEKSI APPS SCRIPT -->
  <script>
    // URL Web App Google Apps Script Terbaru Anda
    const GAS_URL = "https://script.google.com/macros/s/AKfycbzqFCW4lXp0MaXTUZlL0PQtVUR5RYdF5QB0_NiR6jpJzIsS1k59W93lUico8svgEGv5Tw/exec";

    async function handleLogin(e) {
      e.preventDefault();
      
      const btn = document.getElementById("btnLogin");
      const user = document.getElementById("loginUser").value;
      const pass = document.getElementById("loginPass").value;

      // Ubah state tombol saat proses pengiriman
      btn.disabled = true;
      btn.innerHTML = `<i class="fa-solid fa-spinner animate-spin"></i> <span>MEMPROSES...</span>`;

      try {
        const response = await fetch(GAS_URL, {
          method: "POST",
          headers: { "Content-Type": "text/plain;charset=utf-8" },
          body: JSON.stringify({
            action: "login",
            username: user,
            password: pass
          })
        });

        const result = await response.json();

        if (result.status === "success") {
          alert("✅ " + (result.message || "Login Berhasil!"));
          // Logika jika berhasil login (misalnya berpindah halaman/tampilan)
        } else {
          alert("❌ Login Gagal: " + (result.message || "Username atau password salah."));
        }
      } catch (err) {
        alert("⚠️ Terjadi kesalahan koneksi ke server!");
        console.error(err);
      } finally {
        // Kembalikan tombol ke kondisi awal
        btn.disabled = false;
        btn.innerHTML = `<i class="fa-solid fa-right-to-bracket"></i> <span>MASUK APLIKASI</span>`;
      }
    }
  </script>
</body>
</html>
