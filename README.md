<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DeepVision AI | Face Clone Video Call</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #1a365d;
            --secondary: #2d3748;
            --accent: #4299e1;
            --light: #f7fafc;
            --dark: #2d3748;
            --success: #48bb78;
            --warning: #ed8936;
            --danger: #e53e3e;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: var(--light);
            color: var(--dark);
            line-height: 1.6;
        }
        
        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        /* Header */
        header {
            background-color: var(--primary);
            color: white;
            padding: 1rem 0;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }
        
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            color: white;
            text-decoration: none;
        }
        
        .logo span {
            color: var(--accent);
        }
        
        /* Main Content */
        .main-content {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
            margin-top: 30px;
        }
        
        .upload-section, .video-section {
            flex: 1;
            min-width: 300px;
            background: white;
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }
        
        .section-title {
            color: var(--primary);
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid var(--accent);
        }
        
        /* Upload Area */
        .upload-area {
            border: 2px dashed var(--accent);
            border-radius: 8px;
            padding: 30px;
            text-align: center;
            margin-bottom: 20px;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .upload-area:hover {
            background-color: #f1f7ff;
        }
        
        .upload-icon {
            font-size: 50px;
            color: var(--accent);
            margin-bottom: 15px;
        }
        
        .upload-text {
            margin-bottom: 15px;
        }
        
        .btn {
            display: inline-block;
            padding: 0.7rem 1.5rem;
            background-color: var(--accent);
            color: white;
            border-radius: 4px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s;
            border: none;
            cursor: pointer;
        }
        
        .btn:hover {
            background-color: #3182ce;
            transform: translateY(-2px);
        }
        
        .btn-upload {
            background-color: var(--success);
        }
        
        .btn-upload:hover {
            background-color: #38a169;
        }
        
        /* Preview Area */
        .preview-area {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-top: 20px;
        }
        
        .preview-card {
            width: 150px;
            height: 150px;
            border-radius: 8px;
            overflow: hidden;
            position: relative;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
        }
        
        .preview-card img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .remove-btn {
            position: absolute;
            top: 5px;
            right: 5px;
            background: var(--danger);
            color: white;
            width: 25px;
            height: 25px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
        }
        
        /* Video Area */
        .video-container {
            position: relative;
            width: 100%;
            height: 300px;
            background-color: #1a202c;
            border-radius: 8px;
            overflow: hidden;
            margin-bottom: 20px;
        }
        
        .video-feed {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .video-controls {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 20px;
        }
        
        .control-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: var(--primary);
            color: white;
            border: none;
            cursor: pointer;
            font-size: 18px;
            transition: all 0.3s;
        }
        
        .control-btn:hover {
            transform: scale(1.1);
        }
        
        .btn-record {
            background-color: var(--danger);
        }
        
        .btn-record.recording {
            animation: pulse 1.5s infinite;
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }
        
        /* Processing Section */
        .processing-section {
            margin-top: 30px;
            background: white;
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }
        
        .progress-bar {
            height: 10px;
            background-color: #e2e8f0;
            border-radius: 5px;
            margin: 15px 0;
            overflow: hidden;
        }
        
        .progress {
            height: 100%;
            background-color: var(--accent);
            width: 0%;
            transition: width 0.3s;
        }
        
        /* Footer */
        footer {
            background-color: var(--secondary);
            color: white;
            padding: 2rem 0;
            margin-top: 40px;
        }
        
        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 2rem;
        }
        
        .footer-column h3 {
            color: var(--accent);
            margin-bottom: 1.5rem;
            font-size: 1.2rem;
        }
        
        .copyright {
            text-align: center;
            margin-top: 3rem;
            padding-top: 1.5rem;
            border-top: 1px solid #4a5568;
            color: #cbd5e0;
        }
        
        /* Responsive Design */
        @media (max-width: 768px) {
            .main-content {
                flex-direction: column;
            }
            
            .video-container {
                height: 250px;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container">
            <nav>
                <a href="#" class="logo">Clacq D <span>Deep vision test web site </span> </a>
            </nav>
        </div>
    </header>

    <!-- Main Content -->
    <div class="container">
        <div class="main-content">
            <!-- Upload Section -->
            <div class="upload-section">
                <h2 class="section-title">Upload Face Photos</h2>
                <div class="upload-area" id="uploadArea">
                    <div class="upload-icon">
                        <i class="fas fa-cloud-upload-alt"></i>
                    </div>
                    <p class="upload-text">Drag & drop images here or click to browse</p>
                    <button class="btn btn-upload">Select Photos</button>
                    <input type="file" id="fileInput" multiple accept="image/*" style="display: none;">
                </div>
                
                <p>For best results, upload 5-10 photos with different angles and lighting conditions.</p>
                
                <div class="preview-area" id="previewArea">
                    <!-- Preview cards will be added here -->
                </div>
                
                <button class="btn" style="margin-top: 20px; width: 100%;" id="processBtn">
                    <i class="fas fa-cog"></i> Process Face Model
                </button>
            </div>
            
            <!-- Video Section -->
            <div class="video-section">
                <h2 class="section-title">Video Call Interface</h2>
                
                <div class="video-container">
                    <video class="video-feed" id="videoFeed" autoplay muted></video>
                </div>
                
                <div class="video-controls">
                    <button class="control-btn" id="startCamBtn">
                        <i class="fas fa-video"></i>
                    </button>
                    <button class="control-btn btn-record" id="recordBtn">
                        <i class="fas fa-record-vinyl"></i>
                    </button>
                    <button class="control-btn" id="toggleFaceBtn">
                        <i class="fas fa-user"></i>
                    </button>
                </div>
                
                <div style="margin-top: 20px;">
                    <p><strong>Instructions:</strong> Start camera, then click record to begin full-body recording with face replacement.</p>
                </div>
            </div>
        </div>
        
        <!-- Processing Section -->
        <div class="processing-section">
            <h2 class="section-title">Face Model Training</h2>
            
            <div id="modelStatus">Ready to process images...</div>
            <div class="progress-bar">
                <div class="progress" id="progressBar"></div>
            </div>
            
            <div id="trainingDetails">
                <p>Face detection: <span id="faceDetectionStatus">Not started</span></p>
                <p>Feature extraction: <span id="featureExtractionStatus">Not started</span></p>
                <p>Model training: <span id="modelTrainingStatus">Not started</span></p>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>DeepVision AI</h3>
                    <p>Advancing synthetic media technology with ethical responsibility and innovation.</p>
                </div>
                <div class="footer-column">
                    <h3>Legal</h3>
                    <ul>
                        <li><a href="#">Terms of Service</a></li>
                        <li><a href="#">Privacy Policy</a></li>
                        <li><a href="#">Ethical Guidelines</a></li>
                    </ul>
                </div>
            </div>
            <div class="copyright">
                <p>&copy; 2025 DeepVision AI. All rights reserved. Synthetic media technology used responsibly with consent.</p>
            </div>
        </div>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Elements
            const uploadArea = document.getElementById('uploadArea');
            const fileInput = document.getElementById('fileInput');
            const previewArea = document.getElementById('previewArea');
            const processBtn = document.getElementById('processBtn');
            const startCamBtn = document.getElementById('startCamBtn');
            const recordBtn = document.getElementById('recordBtn');
            const toggleFaceBtn = document.getElementById('toggleFaceBtn');
            const videoFeed = document.getElementById('videoFeed');
            const progressBar = document.getElementById('progressBar');
            const faceDetectionStatus = document.getElementById('faceDetectionStatus');
            const featureExtractionStatus = document.getElementById('featureExtractionStatus');
            const modelTrainingStatus = document.getElementById('modelTrainingStatus');
            const modelStatus = document.getElementById('modelStatus');
            
            // State variables
            let isRecording = false;
            let mediaRecorder = null;
            let recordedChunks = [];
            let faceReplacementEnabled = false;
            let stream = null;
            
            // Upload functionality
            uploadArea.addEventListener('click', () => {
                fileInput.click();
            });
            
            fileInput.addEventListener('change', handleFileSelect);
            
            function handleFileSelect(e) {
                const files = e.target.files;
                
                for (let i = 0; i < files.length; i++) {
                    const file = files[i];
                    
                    if (!file.type.match('image.*')) {
                        continue;
                    }
                    
                    const reader = new FileReader();
                    
                    reader.onload = (function(theFile) {
                        return function(e) {
                            // Create preview card
                            const previewCard = document.createElement('div');
                            previewCard.className = 'preview-card';
                            
                            const img = document.createElement('img');
                            img.src = e.target.result;
                            img.title = theFile.name;
                            
                            const removeBtn = document.createElement('div');
                            removeBtn.className = 'remove-btn';
                            removeBtn.innerHTML = '<i class="fas fa-times"></i>';
                            removeBtn.addEventListener('click', function() {
                                previewCard.remove();
                            });
                            
                            previewCard.appendChild(img);
                            previewCard.appendChild(removeBtn);
                            previewArea.appendChild(previewCard);
                        };
                    })(file);
                    
                    reader.readAsDataURL(file);
                }
            }
            
            // Process button
            processBtn.addEventListener('click', function() {
                const previewCards = previewArea.querySelectorAll('.preview-card');
                
                if (previewCards.length === 0) {
                    alert('Please upload at least one image first.');
                    return;
                }
                
                // Simulate processing
                modelStatus.textContent = 'Processing images...';
                
                // Update statuses with delays to simulate processing
                setTimeout(() => {
                    faceDetectionStatus.textContent = 'In progress...';
                    progressBar.style.width = '25%';
                }, 1000);
                
                setTimeout(() => {
                    faceDetectionStatus.textContent = 'Completed (5 faces detected)';
                    featureExtractionStatus.textContent = 'In progress...';
                    progressBar.style.width = '50%';
                }, 3000);
                
                setTimeout(() => {
                    featureExtractionStatus.textContent = 'Completed (128 features extracted)';
                    modelTrainingStatus.textContent = 'In progress...';
                    progressBar.style.width = '75%';
                }, 5000);
                
                setTimeout(() => {
                    modelTrainingStatus.textContent = 'Completed';
                    progressBar.style.width = '100%';
                    modelStatus.textContent = 'Face model ready for video call!';
                    modelStatus.style.color = 'var(--success)';
                    
                    // Enable video controls
                    startCamBtn.disabled = false;
                    recordBtn.disabled = false;
                    toggleFaceBtn.disabled = false;
                }, 7000);
            });
            
            // Camera functionality
            startCamBtn.addEventListener('click', async function() {
                try {
                    stream = await navigator.mediaDevices.getUserMedia({ 
                        video: { width: 1280, height: 720 },
                        audio: true 
                    });
                    
                    videoFeed.srcObject = stream;
                    
                    // Set up media recorder
                    mediaRecorder = new MediaRecorder(stream, {
                        mimeType: 'video/webm;codecs=vp9,opus'
                    });
                    
                    mediaRecorder.ondataavailable = function(event) {
                        if (event.data.size > 0) {
                            recordedChunks.push(event.data);
                        }
                    };
                    
                    mediaRecorder.onstop = function() {
                        const blob = new Blob(recordedChunks, {
                            type: 'video/webm'
                        });
                        
                        const url = URL.createObjectURL(blob);
                        const a = document.createElement('a');
                        a.href = url;
                        a.download = 'deepfake-video-call.webm';
                        a.click();
                        
                        recordedChunks = [];
                    };
                    
                    startCamBtn.innerHTML = '<i class="fas fa-video-slash"></i>';
                    startCamBtn.classList.add('active');
                    
                } catch (err) {
                    console.error('Error accessing camera:', err);
                    alert('Could not access your camera. Please check permissions.');
                }
            });
            
            // Record functionality
            recordBtn.addEventListener('click', function() {
                if (!stream) {
                    alert('Please start your camera first.');
                    return;
                }
                
                if (!isRecording) {
                    // Start recording
                    mediaRecorder.start();
                    isRecording = true;
                    recordBtn.innerHTML = '<i class="fas fa-stop"></i>';
                    recordBtn.classList.add('recording');
                } else {
                    // Stop recording
                    mediaRecorder.stop();
                    isRecording = false;
                    recordBtn.innerHTML = '<i class="fas fa-record-vinyl"></i>';
                    recordBtn.classList.remove('recording');
                }
            });
            
            // Toggle face replacement
            toggleFaceBtn.addEventListener('click', function() {
                faceReplacementEnabled = !faceReplacementEnab
