<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Video Gallery</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body { display: flex; justify-content: center; align-items: center; height: 100vh; background: #000; overflow: hidden; }
        .video-container { position: relative; width: 100vw; height: 56.25vw; overflow: hidden; }
        .video-wrapper { display: flex; width: 1500vw; transition: transform 1s ease-in-out; }
        .video-wrapper iframe {
            width: 100vw; height: 56.25vw; border: none; flex-shrink: 0;
            transition: transform 0.5s ease-in-out;
            transform: scale(0.85); /* Start all videos in a smaller size */
        }
        .video-wrapper .active { transform: scale(1); } /* Full screen video */
    </style>
</head>
<body>
    <div class="video-container">
        <div class="video-wrapper" id="videoWrapper">
            <!-- Replace with proper video links -->
            <iframe class="active" src="https://www.youtube.com/embed/xFGsaePHFHs?autoplay=1&mute=1&controls=0&loop=1&playlist=xFGsaePHFHs"></iframe>
            <iframe src="https://www.youtube.com/embed/IrQuGVq-xTM?autoplay=1&mute=1&controls=0&loop=1&playlist=IrQuGVq-xTM"></iframe>
            <iframe src="https://www.youtube.com/embed/IupEEOP59z4?autoplay=1&mute=1&controls=0&loop=1&playlist=IupEEOP59z4"></iframe>
            <iframe src="https://www.youtube.com/embed/EVVaUJxOdac?autoplay=1&mute=1&controls=0&loop=1&playlist=EVVaUJxOdac"></iframe>
            <!-- Add more videos as needed -->
        </div>
    </div>

    <script>
        let index = 0;
        const videoWrapper = document.getElementById('videoWrapper');
        const iframes = document.querySelectorAll('.video-wrapper iframe');
        
        function switchVideo() {
            // Remove 'active' class from all iframes
            iframes.forEach((iframe) => iframe.classList.remove('active'));

            // Add 'active' class to the current iframe
            iframes[index].classList.add('active');
        }

        // Set the first video as active initially
        switchVideo();

        // Handle scrolling to switch videos
        document.addEventListener('wheel', (event) => {
            if (event.deltaY > 0) {
                // Scroll down, go to the next video
                index = (index + 1) % iframes.length;
            } else {
                // Scroll up, go to the previous video
                index = (index - 1 + iframes.length) % iframes.length;
            }
            switchVideo();
        });
    </script>
</body>
</html>
