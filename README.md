<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tamu</title>
    <style>
        /* General Body Styling */
        body {
            margin: 0;
            padding: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background-color: black;
            font-family: 'Arial', sans-serif;
            overflow: hidden;
        }

        /* Container Styling */
        .container {
            text-align: center;
            color: white;
        }

        /* Text Animation Styling */
        .text-container {
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 2px;
            visibility: hidden;
            margin-bottom: 30px;
        }

        .letter {
            display: inline-block;
            opacity: 0;
        }

        .space {
            width: 0.5rem;
            display: inline-block;
        }

        @keyframes letterEffect {
            0% {
                opacity: 0;
                transform: scale(0.5) rotate(0deg);
            }
            50% {
                opacity: 1;
                transform: scale(1.4) rotate(10deg);
            }
            100% {
                opacity: 1;
                transform: scale(1) rotate(0deg);
            }
        }

        /* Button Styling */
        .button-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            opacity: 0;
            transition: opacity 1s ease-in-out;
        }

        .button {
            background: linear-gradient(135deg, #ff6a00, #ee0979);
            color: white;
            font-size: 1.5rem;
            padding: 12px 30px;
            border: 2px solid transparent;
            cursor: pointer;
            border-radius: 50px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease, background-color 0.3s ease, box-shadow 0.3s ease, border 0.3s ease;
            text-transform: uppercase;
        }

        .button:hover {
            transform: translateY(-5px);
            background: linear-gradient(135deg, #ee0979, #ff6a00);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.4);
            border: 2px solid white;
        }

        .button.no {
            background: linear-gradient(135deg, #f44336, #d32f2f);
        }

        .button.no:hover {
            background: linear-gradient(135deg, #d32f2f, #f44336);
        }

        /* Responsive Styles */
        @media (max-width: 768px) {
            .text-container {
                font-size: 5vw;
            }

            .button {
                font-size: 1.2rem;
            }
        }

        @media (max-width: 480px) {
            .text-container {
                font-size: 7vw;
            }

            .button {
                font-size: 1rem;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div id="text-container" class="text-container"></div>
        <div class="button-container" id="button-container">
            <button class="button" id="yes-btn" aria-label="Yes">Yes</button>
            <button class="button no" id="no-btn" aria-label="No">No</button>
        </div>
    </div>

    <script>
        const textContainer = document.getElementById('text-container');
        const buttonContainer = document.getElementById('button-container');
        const yesButton = document.getElementById('yes-btn');
        const noButton = document.getElementById('no-btn');

        const textSequences = [
            "Tamu, I want to tell you something.!",
            "Can you please give me your friend?"
        ];

        // Function to animate text letter by letter
        function animateText(text, callback) {
            textContainer.innerHTML = '';
            [...text].forEach((char, i) => {
                const span = document.createElement('span');
                span.className = char === ' ' ? 'space' : 'letter';
                span.textContent = char;
                span.style.animation = `letterEffect 0.8s ease ${i * 0.1}s forwards`;
                textContainer.appendChild(span);
            });

            textContainer.style.visibility = 'visible';

            // Trigger callback after animation
            setTimeout(() => callback?.(), text.length * 100 + 1000);
        }

        // Function to display buttons
        function showButtons() {
            buttonContainer.style.opacity = 1;
        }

        // Function to start the sequence
        function startSequence() {
            animateText(textSequences[0], () => {
                animateText(textSequences[1], showButtons);
            });
        }

        // Button Actions
        yesButton.addEventListener('click', () => {
            window.location.href = 'https://t.me/Araf4t1?text=Yes%20I%20will%20give%20you%20my%20friend';
        });

        noButton.addEventListener('click', () => {
            textContainer.innerHTML = 'তামুর বাচ্চা তোর কলিজা দিয়া ভুনা খিচুরি বানামু।';
            buttonContainer.style.display = 'none';
        });

        // Initialize Sequence
        startSequence();
    </script>
</body>
</html>

