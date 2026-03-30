# Facebook-downloader
Facebook downloader
<!DOCTYPE html><html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>FB Video Downloader</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-900 text-white flex items-center justify-center min-h-screen">  <div class="bg-gray-800 p-6 rounded-2xl shadow-xl w-full max-w-md">
    <h1 class="text-2xl font-bold mb-4 text-center">Facebook Video Downloader</h1><input id="url" type="text" placeholder="Masukkan link video Facebook..."
  class="w-full p-3 rounded-lg text-black mb-4" />

<button onclick="downloadVideo()"
  class="w-full bg-blue-500 hover:bg-blue-600 p-3 rounded-lg font-semibold">
  Download
</button>

<div id="result" class="mt-4 text-center"></div>

  </div>  <script>
    async function downloadVideo() {
      const url = document.getElementById('url').value;
      const resultDiv = document.getElementById('result');

      if (!url) {
        resultDiv.innerHTML = "<p class='text-red-400'>Masukkan URL dulu!</p>";
        return;
      }

      resultDiv.innerHTML = "<p>Loading...</p>";

      try {
        // Pakai API gratis (contoh, bisa diganti)
        const api = `https://api.allorigins.win/raw?url=https://fdown.net/download.php?URL=${encodeURIComponent(url)}`;
        
        const res = await fetch(api);
        const text = await res.text();

        resultDiv.innerHTML = `
          <p class='text-green-400'>Klik link di bawah:</p>
          <a href="https://fdown.net/download.php?URL=${encodeURIComponent(url)}" target="_blank"
             class="text-blue-400 underline">Download Video</a>
        `;

      } catch (err) {
        resultDiv.innerHTML = "<p class='text-red-400'>Gagal ambil video.</p>";
      }
    }
  </script></body>
</html>
