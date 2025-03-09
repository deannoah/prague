<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prague</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        :root {
            --primary-color: #4361ee;
            --secondary-color: #f72585;
            --light-color: #f8f9fa;
            --dark-color: #212529;
            --success-color: #4cc9f0;
            --warning-color: #f8961e;
        }
        
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #b5179e, #4361ee);
            min-height: 100vh;
            padding: 20px;
            color: var(--dark-color);
        }
        
        .app-container {
            max-width: 600px;
            margin: 0 auto;
            background-color: rgba(255, 255, 255, 0.95);
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }
        
        .app-header {
            background-color: var(--primary-color);
            color: white;
            padding: 20px;
            text-align: center;
            position: relative;
        }
        
        .app-header h1 {
            font-size: 28px;
            margin-bottom: 5px;
        }
        
        .app-header p {
            font-size: 16px;
            opacity: 0.9;
        }
        
        .prague-icon {
            position: absolute;
            top: 15px;
            right: 15px;
            font-size: 28px;
            color: white;
        }
        
        .app-body {
            padding: 25px;
        }
        
        .input-section, .results-section {
            transition: all 0.3s ease;
        }
        
        .input-section.hidden, .results-section.hidden {
            display: none;
        }
        
        label {
            display: block;
            margin-bottom: 10px;
            font-weight: 600;
            color: var(--primary-color);
        }
        
        textarea {
            width: 100%;
            height: 150px;
            padding: 15px;
            border: 2px solid #ddd;
            border-radius: 10px;
            font-size: 16px;
            transition: border 0.3s;
            resize: none;
        }
        
        textarea:focus {
            border-color: var(--primary-color);
            outline: none;
        }
        
        .instructions {
            margin: 15px 0;
            padding: 15px;
            background-color: #f8f9fa;
            border-left: 4px solid var(--warning-color);
            border-radius: 5px;
        }
        
        .instructions h3 {
            color: var(--warning-color);
            margin-bottom: 8px;
        }
        
        .instructions p {
            font-size: 14px;
            color: #666;
        }
        
        .error-message {
            color: #e63946;
            margin: 10px 0;
            padding: 10px;
            background-color: rgba(230, 57, 70, 0.1);
            border-radius: 5px;
            display: none;
        }
        
        .btn {
            display: block;
            width: 100%;
            padding: 15px;
            margin: 20px 0;
            border: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
            text-align: center;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        .btn-primary {
            background-color: var(--primary-color);
            color: white;
        }
        
        .btn-primary:hover {
            background-color: #3a56d4;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(67, 97, 238, 0.3);
        }
        
        .btn-secondary {
            background-color: var(--secondary-color);
            color: white;
        }
        
        .btn-secondary:hover {
            background-color: #e91c7b;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(247, 37, 133, 0.3);
        }
        
        .apartment-container {
            display: flex;
            flex-direction: column;
            gap: 20px;
            margin-bottom: 20px;
        }
        
        .apartment {
            background: white;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            position: relative;
            overflow: hidden;
        }
        
        .apartment:before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 5px;
            height: 100%;
        }
        
        .apartment:nth-child(1):before {
            background-color: var(--primary-color);
        }
        
        .apartment:nth-child(2):before {
            background-color: var(--secondary-color);
        }
        
        .apartment h3 {
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            font-size: 20px;
        }
        
        .apartment-icon {
            margin-right: 10px;
            width: 30px;
            height: 30px;
            background-color: #f8f9fa;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .apartment:nth-child(1) .apartment-icon {
            color: var(--primary-color);
        }
        
        .apartment:nth-child(2) .apartment-icon {
            color: var(--secondary-color);
        }
        
        .people-list {
            list-style-type: none;
        }
        
        .people-list li {
            padding: 10px 15px;
            margin-bottom: 8px;
            background-color: #f8f9fa;
            border-radius: 5px;
            display: flex;
            align-items: center;
        }
        
        .people-list li:last-child {
            margin-bottom: 0;
        }
        
        .people-list li:before {
            content: '\f007';
            font-family: 'Font Awesome 5 Free';
            margin-right: 10px;
            color: #aaa;
        }
        
        .confetti {
            position: fixed;
            width: 10px;
            height: 10px;
            background-color: #f00;
            animation: fall 3s linear forwards;
            z-index: 1000;
        }
        
        @keyframes fall {
            to {
                transform: translateY(100vh);
            }
        }
        
        .footer {
            text-align: center;
            padding: 15px;
            font-size: 14px;
            color: rgba(255, 255, 255, 0.8);
        }
        
        @media (min-width: 768px) {
            .apartment-container {
                flex-direction: row;
            }
            
            .apartment {
                flex: 1;
            }
        }
    </style>
</head>
<body>
    <div class="app-container">
        <div class="app-header">
            <h1>Bachelor Party Prague</h1>
            <p>Randomly split your group between two apartments</p>
            <div class="prague-icon">
                <i class="fas fa-building"></i>
            </div>
        </div>
        
        <div class="app-body">
            <div class="input-section" id="inputSection">
                <label for="names">Enter everyone's names (one per line):</label>
                <textarea id="names" placeholder="John
Jane
Alex
..."></textarea>
                
                <div class="instructions">
                    <h3><i class="fas fa-info-circle"></i> Instructions</h3>
                    <p>Enter each person's name on a new line. You can enter between 2 and 16 people. 
                       <br><strong>Special rules:</strong>
                       <br>• If 3 or fewer people: everyone stays in Apartment 1
                       <br>• If exactly 4 people: split 2 and 2 between apartments
                       <br>• No apartment will ever have just 1 person
                       <br>• "Dar" and "Mor" will always be placed in the same apartment
                       <br>&nbsp;&nbsp;(Also recognizes "דר" and "מור")
                    </p>
                </div>
                
                <div class="error-message" id="errorMessage"></div>
                
                <button class="btn btn-primary" onclick="splitGroups()">
                    <i class="fas fa-random"></i> Split The Group
                </button>
            </div>
            
            <div class="results-section hidden" id="resultsSection">
                <div class="apartment-container" id="apartmentContainer">
                    <div class="apartment">
                        <h3>
                            <div class="apartment-icon">
                                <i class="fas fa-home"></i>
                            </div>
                            Apartment 1
                        </h3>
                        <ul class="people-list" id="apartment1"></ul>
                    </div>
                    
                    <div class="apartment">
                        <h3>
                            <div class="apartment-icon">
                                <i class="fas fa-home"></i>
                            </div>
                            Apartment 2
                        </h3>
                        <ul class="people-list" id="apartment2"></ul>
                    </div>
                </div>
                
                <button class="btn btn-secondary" onclick="resetApp()">
                    <i class="fas fa-redo-alt"></i> Create New Split
                </button>
            </div>
        </div>
    </div>
    
    <div class="footer">
        
    </div>
    
    <script>
        function splitGroups() {
            // Get names from textarea
            const namesText = document.getElementById('names').value.trim();
            const namesList = namesText.split('\n').filter(name => name.trim() !== '');
            
            // Validate input
            const errorMessage = document.getElementById('errorMessage');
            
            if (namesList.length < 2) {
                errorMessage.textContent = 'Please enter at least 2 names.';
                errorMessage.style.display = 'block';
                return;
            }
            
            if (namesList.length > 16) {
                errorMessage.textContent = 'Please enter no more than 16 names.';
                errorMessage.style.display = 'block';
                return;
            }
            
            // Hide error message if validation passes
            errorMessage.style.display = 'none';
            
            // If 3 or fewer people, put everyone in Apartment 1
            if (namesList.length <= 3) {
                const apartment1 = [...namesList];
                const apartment2 = [];
                
                // Display results with animation
                displayResults(apartment1, apartment2);
                return;
            }
            
            // Special case for exactly 4 people: split 2 and 2
            if (namesList.length === 4) {
                // Check if Dar and Mor are in the list (both English and Hebrew spellings)
                const hasDar = namesList.some(name => 
                    name.trim().toLowerCase() === "dar" || name.trim() === "דר");
                const hasMor = namesList.some(name => 
                    name.trim().toLowerCase() === "mor" || name.trim() === "מור");
                
                // If both Dar and Mor are present, keep them together
                if (hasDar && hasMor) {
                    const otherNames = namesList.filter(name => 
                        (name.trim().toLowerCase() !== "dar" && name.trim() !== "דר") && 
                        (name.trim().toLowerCase() !== "mor" && name.trim() !== "מור")
                    );
                    
                    // Randomly decide which apartment gets Dar and Mor
                    if (Math.random() < 0.5) {
                        const apartment1 = ["Dar", "Mor"];
                        const apartment2 = otherNames;
                        displayResults(apartment1, apartment2);
                    } else {
                        const apartment1 = otherNames;
                        const apartment2 = ["Dar", "Mor"];
                        displayResults(apartment1, apartment2);
                    }
                } else {
                    // Shuffle the names
                    const shuffledNames = [...namesList];
                    for (let i = shuffledNames.length - 1; i > 0; i--) {
                        const j = Math.floor(Math.random() * (i + 1));
                        [shuffledNames[i], shuffledNames[j]] = [shuffledNames[j], shuffledNames[i]];
                    }
                    
                    // Split 2 and 2
                    const apartment1 = shuffledNames.slice(0, 2);
                    const apartment2 = shuffledNames.slice(2, 4);
                    displayResults(apartment1, apartment2);
                }
                return;
            }
            
            // Shuffle the names using Fisher-Yates algorithm
            const shuffledNames = [...namesList];
            for (let i = shuffledNames.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [shuffledNames[i], shuffledNames[j]] = [shuffledNames[j], shuffledNames[i]];
            }
            
            // Check if Dar and Mor are in the list (both English and Hebrew spellings)
            const darIndex = shuffledNames.findIndex(name => 
                name.trim().toLowerCase() === "dar" || name.trim() === "דר");
            const morIndex = shuffledNames.findIndex(name => 
                name.trim().toLowerCase() === "mor" || name.trim() === "מור");
            const hasDarAndMor = darIndex !== -1 && morIndex !== -1;
            
            // Calculate split point (handling odd numbers)
            const midpoint = Math.floor(shuffledNames.length / 2);
            
            // Split into two apartments
            let apartment1 = [];
            let apartment2 = [];
            
            if (hasDarAndMor) {
                // Ensure Dar and Mor are in the same apartment
                // First, remove them from the shuffled array
                const specialNames = [];
                if (darIndex !== -1) {
                    specialNames.push(shuffledNames.splice(darIndex, 1)[0]);
                }
                
                // Need to recalculate morIndex as removing Dar may have shifted indices
                const newMorIndex = shuffledNames.findIndex(name => 
                    name.trim().toLowerCase() === "mor" || name.trim() === "מור");
                if (newMorIndex !== -1) {
                    specialNames.push(shuffledNames.splice(newMorIndex, 1)[0]);
                }
                
                // Recalculate midpoint with remaining names
                const remainingMidpoint = Math.floor(shuffledNames.length / 2);
                
                // Split remaining names
                apartment1 = shuffledNames.slice(0, remainingMidpoint);
                apartment2 = shuffledNames.slice(remainingMidpoint);
                
                // Ensure no apartment has just 1 person
                if (apartment1.length === 1 && apartment2.length >= 3) {
                    // Move one person from apartment2 to apartment1
                    apartment1.push(apartment2.pop());
                } else if (apartment2.length === 1 && apartment1.length >= 3) {
                    // Move one person from apartment1 to apartment2
                    apartment2.push(apartment1.pop());
                }
                
                // Randomly decide which apartment gets Dar and Mor
                if (Math.random() < 0.5) {
                    apartment1 = apartment1.concat(specialNames);
                } else {
                    apartment2 = apartment2.concat(specialNames);
                }
            } else {
                // Normal split
                apartment1 = shuffledNames.slice(0, midpoint);
                apartment2 = shuffledNames.slice(midpoint);
                
                // Ensure no apartment has just 1 person
                if (apartment1.length === 1 && apartment2.length >= 3) {
                    // Move one person from apartment2 to apartment1
                    apartment1.push(apartment2.pop());
                } else if (apartment2.length === 1 && apartment1.length >= 3) {
                    // Move one person from apartment1 to apartment2
                    apartment2.push(apartment1.pop());
                }
            }
            
            // Display results with animation
            displayResults(apartment1, apartment2);
        }
        
        function displayResults(apartment1, apartment2) {
            // Clear previous results
            document.getElementById('apartment1').innerHTML = '';
            document.getElementById('apartment2').innerHTML = '';
            
            // Prepare the animation container
            const animationContainer = document.createElement('div');
            animationContainer.className = 'animation-container';
            animationContainer.style.position = 'fixed';
            animationContainer.style.top = '0';
            animationContainer.style.left = '0';
            animationContainer.style.width = '100%';
            animationContainer.style.height = '100%';
            animationContainer.style.backgroundColor = 'rgba(0, 0, 0, 0.7)';
            animationContainer.style.zIndex = '1000';
            animationContainer.style.display = 'flex';
            animationContainer.style.justifyContent = 'center';
            animationContainer.style.alignItems = 'center';
            animationContainer.style.flexDirection = 'column';
            document.body.appendChild(animationContainer);
            
            // Create animation title
            const animTitle = document.createElement('h2');
            animTitle.textContent = 'Bachelor Party Draw';
            animTitle.style.color = 'white';
            animTitle.style.marginBottom = '10px';
            animTitle.style.fontSize = '28px';
            animTitle.style.textShadow = '0 0 10px rgba(255,215,0,0.7)';
            animationContainer.appendChild(animTitle);
            
            // Create animation subtitle
            const animSubtitle = document.createElement('p');
            animSubtitle.textContent = 'Apartment Assignment Draw';
            animSubtitle.style.color = 'gold';
            animSubtitle.style.marginBottom = '20px';
            animSubtitle.style.fontSize = '18px';
            animationContainer.appendChild(animSubtitle);
            
            // Create name container
            const nameContainer = document.createElement('div');
            nameContainer.style.display = 'flex';
            nameContainer.style.flexDirection = 'column';
            nameContainer.style.alignItems = 'center';
            nameContainer.style.maxWidth = '90%';
            animationContainer.appendChild(nameContainer);
            
            // Interleave names from apartment1 and apartment2 for alternating display
            const interleavedNames = [];
            const maxLength = Math.max(apartment1.length, apartment2.length);
            
            for (let i = 0; i < maxLength; i++) {
                if (i < apartment1.length) {
                    interleavedNames.push({name: apartment1[i], apartment: 1});
                }
                
                if (i < apartment2.length) {
                    interleavedNames.push({name: apartment2[i], apartment: 2});
                }
            }
            
            // Shuffle the interleaved names to randomize the order of the draw
            for (let i = interleavedNames.length - 1; i > 0; i--) {
                const j = Math.floor(Math.random() * (i + 1));
                [interleavedNames[i], interleavedNames[j]] = [interleavedNames[j], interleavedNames[i]];
            }
            
            // Create lottery machine container
            const lotteryContainer = document.createElement('div');
            lotteryContainer.style.width = '150px';
            lotteryContainer.style.height = '150px';
            lotteryContainer.style.backgroundColor = '#333';
            lotteryContainer.style.borderRadius = '50%';
            lotteryContainer.style.position = 'relative';
            lotteryContainer.style.marginBottom = '25px';
            lotteryContainer.style.overflow = 'hidden';
            lotteryContainer.style.boxShadow = '0 5px 15px rgba(0,0,0,0.5), inset 0 -10px 20px rgba(0,0,0,0.3)';
            lotteryContainer.style.border = '5px solid gold';
            animationContainer.insertBefore(lotteryContainer, nameContainer);
            
            // Create lottery balls (will be animated during the draw)
            const ballColors = ['#4361ee', '#f72585', '#4cc9f0', '#7209b7', '#3a0ca3', '#4895ef'];
            const balls = [];
            
            for (let i = 0; i < 10; i++) {
                const ball = document.createElement('div');
                ball.style.width = '30px';
                ball.style.height = '30px';
                ball.style.backgroundColor = ballColors[i % ballColors.length];
                ball.style.borderRadius = '50%';
                ball.style.position = 'absolute';
                ball.style.transform = `translate(${Math.random() * 100 - 50}px, ${Math.random() * 100 - 50}px)`;
                ball.style.transition = 'transform 0.3s';
                balls.push(ball);
                lotteryContainer.appendChild(ball);
            }
            
            // Animation function
            const animateNames = (index) => {
                if (index >= interleavedNames.length) {
                    // Animation complete
                    setTimeout(() => {
                        // Remove animation container
                        animationContainer.remove();
                        
                        // Display final results
                        apartment1.forEach(name => {
                            const li = document.createElement('li');
                            li.textContent = name;
                            document.getElementById('apartment1').appendChild(li);
                        });
                        
                        apartment2.forEach(name => {
                            const li = document.createElement('li');
                            li.textContent = name;
                            document.getElementById('apartment2').appendChild(li);
                        });
                        
                        // Hide input section and show results section
                        document.getElementById('inputSection').classList.add('hidden');
                        document.getElementById('resultsSection').classList.remove('hidden');
                        
                        // Create confetti effect
                        createConfetti();
                    }, 500);
                    return;
                }
                
                // Animate lottery balls randomly
                balls.forEach(ball => {
                    ball.style.transform = `translate(${Math.random() * 100 - 50}px, ${Math.random() * 100 - 50}px)`;
                });
                
                // Current name and apartment
                const {name, apartment} = interleavedNames[index];
                
                // Create selected ball that will emerge from the lottery machine
                const selectedBall = document.createElement('div');
                selectedBall.style.width = '40px';
                selectedBall.style.height = '40px';
                selectedBall.style.backgroundColor = apartment === 1 ? '#4361ee' : '#f72585';
                selectedBall.style.color = 'white';
                selectedBall.style.borderRadius = '50%';
                selectedBall.style.position = 'absolute';
                selectedBall.style.left = '50%';
                selectedBall.style.top = '50%';
                selectedBall.style.transform = 'translate(-50%, -50%) scale(0.5)';
                selectedBall.style.transition = 'all 0.3s';
                selectedBall.style.zIndex = '10';
                selectedBall.style.display = 'flex';
                selectedBall.style.alignItems = 'center';
                selectedBall.style.justifyContent = 'center';
                selectedBall.style.fontWeight = 'bold';
                selectedBall.style.fontSize = '14px';
                selectedBall.textContent = index + 1;
                lotteryContainer.appendChild(selectedBall);
                
                // Create name element
                const nameElem = document.createElement('div');
                nameElem.textContent = name;
                nameElem.style.padding = '15px 30px';
                nameElem.style.backgroundColor = 'white';
                nameElem.style.borderRadius = '8px';
                nameElem.style.margin = '5px';
                nameElem.style.fontWeight = 'bold';
                nameElem.style.fontSize = '18px';
                nameElem.style.width = '80%';
                nameElem.style.textAlign = 'center';
                nameElem.style.transform = 'scale(0)';
                nameElem.style.transition = 'transform 0.2s, background-color 0.3s';
                nameContainer.appendChild(nameElem);
                
                // Ball movement animation
                setTimeout(() => {
                    selectedBall.style.transform = 'translate(-50%, 100px) scale(1)';
                    
                    // Appear animation for name
                    setTimeout(() => {
                        nameElem.style.transform = 'scale(1)';
                        
                        // Decision animation
                        setTimeout(() => {
                            // Style based on apartment assignment
                            if (apartment === 1) {
                                nameElem.style.backgroundColor = '#4361ee';
                                nameElem.style.color = 'white';
                                nameElem.textContent = `${name} → Apartment 1`;
                            } else {
                                nameElem.style.backgroundColor = '#f72585';
                                nameElem.style.color = 'white';
                                nameElem.textContent = `${name} → Apartment 2`;
                            }
                            
                            // Remove the selected ball
                            setTimeout(() => {
                                selectedBall.remove();
                                
                                // Move to next name
                                setTimeout(() => {
                                    animateNames(index + 1);
                                }, 200);
                            }, 100);
                        }, 300);
                    }, 150);
                }, 150);
            };
            
            // Start animation
            animateNames(0);
        }
        
        function resetApp() {
            // Clear the textarea
            document.getElementById('names').value = '';
            
            // Hide results section and show input section
            document.getElementById('resultsSection').classList.add('hidden');
            document.getElementById('inputSection').classList.remove('hidden');
            
            // Remove any existing confetti
            const confetti = document.querySelectorAll('.confetti');
            confetti.forEach(c => c.remove());
        }
        
        function createConfetti() {
            const colors = ['#4361ee', '#f72585', '#4cc9f0', '#7209b7', '#3a0ca3', '#4895ef'];
            
            for (let i = 0; i < 100; i++) {
                const confetti = document.createElement('div');
                confetti.className = 'confetti';
                
                // Random position
                confetti.style.left = Math.random() * 100 + 'vw';
                confetti.style.top = -20 + 'px';
                
                // Random size
                const size = Math.random() * 10 + 5;
                confetti.style.width = size + 'px';
                confetti.style.height = size + 'px';
                
                // Random color
                confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                
                // Random rotation
                confetti.style.transform = `rotate(${Math.random() * 360}deg)`;
                
                // Random shape
                const shapes = ['circle', 'square', 'triangle'];
                const shape = shapes[Math.floor(Math.random() * shapes.length)];
                
                if (shape === 'circle') {
                    confetti.style.borderRadius = '50%';
                } else if (shape === 'triangle') {
                    confetti.style.width = '0';
                    confetti.style.height = '0';
                    confetti.style.backgroundColor = 'transparent';
                    confetti.style.borderLeft = `${size/2}px solid transparent`;
                    confetti.style.borderRight = `${size/2}px solid transparent`;
                    confetti.style.borderBottom = `${size}px solid ${colors[Math.floor(Math.random() * colors.length)]}`;
                }
                
                // Random duration
                const duration = Math.random() * 3 + 2;
                confetti.style.animationDuration = duration + 's';
                
                // Add to body
                document.body.appendChild(confetti);
                
                // Remove after animation
                setTimeout(() => {
                    confetti.remove();
                }, duration * 1000);
            }
        }
    </script>
</body>
</html>
