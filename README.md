<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Human Verification</title>
  <!-- Tailwind CSS -->
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
  <!-- AOS Library -->
  <link href="https://cdn.jsdelivr.net/npm/aos@2.3.4/dist/aos.css" rel="stylesheet">
  <style>
    audio {
      display: none;
    }
    .loading {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(255, 255, 255, 0.8);
      z-index: 50;
      justify-content: center;
      align-items: center;
    }
    .spinner {
      border: 8px solid rgba(0, 0, 0, 0.1);
      border-left-color: #6366F1; /* Indigo color */
      border-radius: 50%;
      width: 64px;
      height: 64px;
      animation: spin 1s linear infinite;
    }
    @keyframes spin {
      0% {
        transform: rotate(0deg);
      }
      100% {
        transform: rotate(360deg);
      }
    }
  </style>
</head>
<body class="bg-gray-100 flex items-center justify-center min-h-screen">

  <!-- Backsound -->
  <audio id="backsound" loop>
    <source src="whoevermoveisgay.mp4" type="audio/mpeg">
    Your browser does not support the audio element.
  </audio>

  <div class="bg-white p-8 rounded-lg shadow-lg max-w-sm w-full" data-aos="fade-up">
    <h2 class="text-2xl font-bold mb-4 text-center">Human Verification</h2>
    <p class="mb-4 text-center">Please verify that you are human</p>
    <form id="verification-form">
      <div class="mb-4">
        <label for="language" class="block text-sm font-medium text-gray-700">English or Spanish?</label>
        <input type="text" id="language" name="language" class="mt-1 block w-full px-3 py-2 border border-gray-300 rounded-md shadow-sm focus:outline-none focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm" placeholder="Your answer">
      </div>
      <button type="submit" class="w-full bg-indigo-600 text-white py-2 px-4 rounded-md hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2">Verify</button>
    </form>
  </div>

  <div id="loading" class="loading flex">
    <div class="spinner"></div>
  </div>

  <!-- AOS Library -->
  <script src="https://cdn.jsdelivr.net/npm/aos@2.3.4/dist/aos.js"></script>
  <script>
    AOS.init();
  </script>
  <script>
    document.getElementById('verification-form').addEventListener('submit', function(event) {
      event.preventDefault();
      var answer = document.getElementById('language').value.trim().toLowerCase();
      
      // Show loading
      document.getElementById('loading').style.display = 'flex';

      setTimeout(function() { // Simulating a delay for demonstration
        if (answer === 'english' || answer === 'spanish') {
          window.location.href = 'Walaa.html';
        } else {
          document.getElementById('loading').style.display = 'none';
          alert('Please answer with "English" or "Spanish".');
        }
      }, 1000); // 1 second delay for demo purposes
    });

    document.getElementById('language').addEventListener('input', function() {
      var audio = document.getElementById('backsound');
      if (audio.paused) {
        audio.play().catch(error => {
          console.log('Auto-play was prevented:', error);
        });
      }
    });
  </script>
</body>
</html>
