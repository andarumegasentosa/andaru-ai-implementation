# Panduan Penggunaan File `andaru.md` sebagai Konteks AI

File `andaru.md` berisi profil lengkap PT Andaru Mega Sentosa — mulai dari deskripsi perusahaan, produk, portofolio proyek, target audiens, hingga analisa pasar. File ini dirancang untuk digunakan sebagai **konteks perusahaan** saat berkomunikasi dengan AI provider seperti Gemini, ChatGPT, Claude, dan lainnya.

---

## Cara Penggunaan

### Metode 1 — Attachment Langsung (Paling Mudah)

Cocok untuk: Gemini, ChatGPT, Claude (versi web)

1. Buka platform AI (contoh: [gemini.google.com](https://gemini.google.com))
2. Klik ikon **attachment / lampiran** di kolom chat
3. Upload file `andaru.md`
4. Ketik prompt kamu setelah file ter-upload

**Contoh prompt setelah attach:**
```
Buatkan 10 ide konten Instagram yang cocok untuk perusahaan saya berdasarkan file yang saya lampirkan.
```

```
Buatkan strategi iklan Meta Ads lengkap untuk perusahaan saya. Fokus pada segmen cold storage dan industri makanan.
```

---

### Metode 2 — Copy-Paste Isi File (Universal)

Cocok untuk: semua platform AI, termasuk yang tidak mendukung attachment

1. Buka file `andaru.md` dengan teks editor (Notepad, VS Code, dll)
2. Pilih semua teks (`Ctrl+A`) lalu copy (`Ctrl+C`)
3. Paste ke kolom chat AI, lalu tambahkan prompt kamu di bawahnya

**Template prompt:**
```
Berikut adalah profil perusahaan saya:

[PASTE ISI andaru.md DI SINI]

---

Berdasarkan informasi di atas, [tulis permintaan kamu di sini].
```

---

### Metode 3 — Sebagai System Prompt (API / Developer)

Cocok untuk: developer yang mengintegrasikan AI ke aplikasi atau workflow otomatis

Masukkan isi `andaru.md` sebagai **system message** di API call:

```python
# Contoh menggunakan Google Gemini API (Python)
import google.generativeai as genai

with open("context/andaru.md", "r", encoding="utf-8") as f:
    company_context = f.read()

model = genai.GenerativeModel("gemini-1.5-pro")
chat = model.start_chat(history=[])

system_prompt = f"""
Kamu adalah asisten bisnis untuk PT Andaru Mega Sentosa.
Gunakan informasi berikut sebagai konteks perusahaan dalam setiap jawaban:

{company_context}
"""

response = chat.send_message(system_prompt + "\n\n" + "Buatkan strategi Meta Ads untuk bulan ini.")
print(response.text)
```

```javascript
// Contoh menggunakan OpenAI API (Node.js)
import OpenAI from "openai";
import fs from "fs";

const client = new OpenAI();
const companyContext = fs.readFileSync("context/andaru.md", "utf-8");

const response = await client.chat.completions.create({
  model: "gpt-4o",
  messages: [
    {
      role: "system",
      content: `Kamu adalah asisten bisnis PT Andaru Mega Sentosa. Berikut profil perusahaan:\n\n${companyContext}`,
    },
    {
      role: "user",
      content: "Buatkan 5 ide konten TikTok yang viral untuk produk cold storage kami.",
    },
  ],
});

console.log(response.choices[0].message.content);
```

---

## Ide Prompt yang Bisa Langsung Digunakan

### Konten & Marketing
```
Buatkan 10 ide konten Instagram untuk PT Andaru yang menarget pemilik pabrik makanan.
```
```
Buatkan caption Instagram untuk memperkenalkan produk PUR Panel cold storage kami.
```
```
Buatkan skrip video TikTok 60 detik yang memperlihatkan keunggulan sandwich panel dibanding material konvensional.
```

### Iklan (Meta Ads / Google Ads)
```
Buatkan strategi kampanye Meta Ads untuk Andaru, fokus pada segmen industri makanan & minuman di Jawa Barat.
```
```
Tulis 3 variasi teks iklan Facebook Ads untuk produk cold storage panel PUR kami. Target audiens: pengusaha cold storage.
```
```
Rekomendasikan struktur campaign Google Ads untuk Andaru — dari keyword, ad group, hingga landing page.
```

### Strategi Bisnis
```
Analisa peluang ekspansi Andaru ke pasar Kalimantan berdasarkan profil perusahaan ini.
```
```
Buatkan script untuk sales call ke calon klien pabrik snack yang belum pernah pakai sandwich panel.
```
```
Buat template email penawaran untuk kontraktor yang sedang tender proyek pabrik baru.
```

### Edukasi & Blog
```
Buatkan outline artikel blog: "Mengapa Pabrik Makanan Wajib Pakai Sandwich Panel AZ100 Antibacterial?"
```
```
Jelaskan perbedaan EPS vs PUR panel dalam bahasa yang mudah dipahami pemilik UMKM pangan.
```

---

## Tips Penggunaan

- **Semakin spesifik promptnya, semakin baik hasilnya.** Sebutkan platform, target audiens, dan tujuan secara eksplisit.
- **Iterasi.** Gunakan output pertama sebagai draft, lalu minta AI untuk merevisi atau memperdalam bagian tertentu.
- **Gabungkan dengan data baru.** Jika ada proyek terbaru atau produk baru, tambahkan informasinya ke prompt agar output lebih relevan.
- **Update `andaru.md` secara berkala** jika ada perubahan data perusahaan (proyek baru, produk baru, target pasar baru).

---