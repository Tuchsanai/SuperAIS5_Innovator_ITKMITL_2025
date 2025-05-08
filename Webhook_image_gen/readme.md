```
create html code for image generation from text project with javascript and css styles.  The input from text is send to web hook server with POST request
to url=xxx and then receive respond from web hook server and show image in page


```


```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Text to Image Generator</title>
</head>
<body>
  <h2>Text to Image Generator</h2>
  <input type="text" id="promptInput" placeholder="Enter your prompt" size="50">
  <button onclick="generateImage()">Generate Image</button>

  <div id="result" style="margin-top: 20px;">
    <p><strong>Generated Image:</strong></p>
    <img id="outputImage" src="" alt="Image will appear here" style="max-width: 100%; border: 1px solid #ccc; display: none;">
  </div>

  <script>
    async function generateImage() {
      const prompt = document.getElementById('promptInput').value;
      const resultImage = document.getElementById('outputImage');
      const resultDiv = document.getElementById('result');

      if (!prompt) {
        alert("Please enter a prompt.");
        return;
      }

      try {
        const response = await fetch('YOUR_WEBHOOK_URL_HERE', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json'
          },
          body: JSON.stringify({ text: prompt })
        });

        const data = await response.json();

        // Assume webhook returns base64 or direct image URL
        if (data.image_base64) {
          resultImage.src = `data:image/png;base64,${data.image_base64}`;
        } else if (data.image_url) {
          resultImage.src = data.image_url;
        } else {
          throw new Error("No image data found in response.");
        }

        resultImage.style.display = "block";
      } catch (err) {
        console.error(err);
        alert("Error generating image.");
      }
    }
  </script>
</body>
</html>


```