<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>hey</h1>
    <video id="video"></video>
    <script>

navigator.mediaDevices.getUserMedia({ video: true })
  .then(function(stream) {
    var videoElement = document.getElementById('video');

    // Set the video stream as the source for the video element
    videoElement.srcObject = stream;
    videoElement.play();
  })
  .catch(function(error) {
    console.log('Error accessing camera:', error);
  });


</script>

<video id="video" autoplay></video>
<canvas id="canvas"></canvas>
<button id="captureBtn">Capture</button>

<script>
  var videoElement = document.getElementById('video');
  var canvasElement = document.getElementById('canvas');
  var captureBtn = document.getElementById('captureBtn');

  captureBtn.addEventListener('click', function() {
    var context = canvasElement.getContext('2d');
    context.drawImage(videoElement, 0, 0, canvasElement.width, canvasElement.height);
  });

  navigator.mediaDevices.getUserMedia({ video: true })
    .then(function(stream) {
      videoElement.srcObject = stream;
    })
    .catch(function(error) {
      console.log('Error accessing camera:', error);
    });
</script>


</body>
</html>
