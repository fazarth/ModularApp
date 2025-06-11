# 🧪 Modular App Generator (.NET 8 + SQLite + GitHub Codespaces)

## 📌 Tujuan Proyek

Sebuah **aplikasi generator berbasis Modular Architecture** menggunakan .NET 8 + SQLite + EF Core. Cocok untuk:

* Latihan arsitektur scalable
* Portofolio backend
* Dasar untuk berbagai jenis aplikasi CRUD

---

## ✅ Fitur Utama

* Modular: User dapat menentukan nama aplikasi dan modul-modulnya
* CRUD Generator per modul (Controller, Service, Entity)
* EF Core dengan SQLite (mudah diganti ke SQL Server)
* Siap pakai di **GitHub Codespaces** (no install required)
* CICD (Build + Format + Test) via GitHub Actions

---

## 🧰 Prasyarat

* Akun GitHub (aktifkan Codespaces)
* [.NET 8 SDK](https://dotnet.microsoft.com/en-us/download) *(sudah tersedia di Codespaces)*
* GitHub CLI *(jika clone via terminal)*

---

## 🚀 Setup Project

### 1. Clone Repo dan Buka dengan Codespaces

```bash
git clone https://github.com/namamu/AppGenerator.git
cd AppGenerator
gh codespace create --repo namamu/AppGenerator --branch main
```

> Atau langsung klik tombol "Code > Codespaces" di GitHub UI

### 2. Jalankan Proyek

```bash
dotnet run --project src/AppGenerator
```

### 3. Contoh Generate Aplikasi

```http
GET /generate?name=InventoryApp&modules=Users,Orders,Products
```

Hasil: folder `Generated/InventoryApp/Modules/...`

---

## 🧱 Struktur Folder

```
AppGenerator/
┣ 📁 src/
┃ ┗ 📁 AppGenerator/         ← Project utama
┃     ┣ Program.cs
┃     ┣ IGeneratorService.cs
┃     ┗ GeneratorService.cs
┣ 📁 Templates/              ← Template modul
┣ 📁 Generated/              ← Output aplikasi yang digenerate
┣ 📄 .github/workflows/ci.yml ← CICD pipeline
┣ 📄 README.md
```

---

## 🔄 Ganti ke SQL Server

Ubah di `Program.cs`:

```csharp
options.UseSqlite("Data Source=app.db"); // ← default
```

menjadi:

```csharp
options.UseSqlServer("Server=xxx;Database=xxx;User Id=...;");
```

Lalu jalankan:

```bash
dotnet ef migrations add Init
```

---

## ⚙️ GitHub Actions (CICD)

File: `.github/workflows/ci.yml`

* Format check: `dotnet format`
* Build check: `dotnet build`
* Test: `dotnet test` *(jika ada unit test)*

---

## 📦 Rencana Modular

* [x] User dapat beri nama app sendiri
* [x] CRUD generator otomatis per modul
* [x] Clean folder per modul
* [ ] Auth module (JWT)
* [ ] Custom validation per modul
* [ ] Export ke ZIP

---

## 🧠 Tips Pengembangan

* Tambah folder `Templates/ModulBase/` → sebagai blueprint modul
* Di `GeneratorService.cs`, gunakan `System.IO` dan string interpolation untuk buat file
* Pakai `Regex` untuk ganti namespace/template jika perlu

---

## 📚 Referensi

* [.NET Minimal API](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/minimal-apis)
* [EF Core SQLite](https://learn.microsoft.com/en-us/ef/core/providers/sqlite/?tabs=dotnet-core-cli)
* [GitHub Codespaces](https://github.com/features/codespaces)
* [GitHub Actions](https://docs.github.com/en/actions)

---
