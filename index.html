<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="theme-color" content="#1e293b">
    <title>Smart Dryer Control</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="manifest" href="/LoneRangeGamer/manifest.json">
    <link rel="apple-touch-icon" href="/LoneRangeGamer/icons/icon-192x192.png">
    <style>
        body { font-family: 'Inter', sans-serif; }
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700;800&display=swap');
        .screen { display: none; }
        .screen.active { display: flex; }
        .modal-bg {
            background-color: rgba(0, 0, 0, 0.5);
            transition: opacity 0.3s ease;
        }
        .modal-content {
            transition: transform 0.3s ease;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 300px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
            max-height: 80vw;
        }
        @media (min-width: 768px) {
            .chart-container { max-height: 300px; }
        }
    </style>
</head>
<body class="bg-stone-100 text-stone-800 flex items-center justify-center min-h-screen">

    <div class="w-full max-w-md mx-auto bg-stone-50 shadow-2xl rounded-3xl overflow-hidden h-[80vh] min-h-[600px] max-h-[800px] flex flex-col">

        <!-- Splash Screen -->
        <div id="screen-splash" class="screen active flex-col items-center justify-center w-full h-full bg-slate-800 text-white">
            <div class="w-24 h-24 border-4 border-t-4 border-t-cyan-400 border-slate-600 rounded-full animate-spin"></div>
            <h1 class="text-3xl font-bold mt-6">SmartDry</h1>
            <p class="text-slate-400">Effortless Laundry, Smarter Living.</p>
        </div>

        <!-- Bluetooth Connection Screen -->
        <div id="screen-bluetooth" class="screen flex-col items-center justify-center w-full h-full p-6 text-center">
            <h2 class="text-2xl font-bold text-slate-800">Connect Your Dryer</h2>
            <p class="text-stone-500 mt-2 mb-6">First, let's pair your dryer using Bluetooth.</p>
            <div id="bluetooth-initial-view">
                <div class="w-20 h-20 mx-auto bg-cyan-100 text-cyan-600 rounded-full flex items-center justify-center text-4xl mb-6">B</div>
                <p class="text-sm text-stone-600 mb-4">1. Ensure your dryer's Bluetooth is enabled.</p>
                <button id="scan-btn" class="w-full bg-slate-800 text-white font-bold py-3 px-4 rounded-xl hover:bg-slate-700 transition-colors">Scan for Dryers</button>
            </div>
            <div id="bluetooth-scan-view" class="hidden w-full">
                 <div class="w-full text-left">
                    <p class="font-bold mb-2">Searching for devices...</p>
                    <div class="space-y-2" id="devices-list"></div>
                 </div>
            </div>
             <div id="bluetooth-connecting-view" class="hidden w-full">
                <div class="w-16 h-16 border-4 border-t-4 border-t-cyan-500 border-stone-200 rounded-full animate-spin mx-auto mb-4"></div>
                <p class="text-lg font-semibold text-stone-700">Connecting to <span id="connecting-device-name"></span>...</p>
            </div>
        </div>

        <!-- Home/Dashboard Screen -->
        <div id="screen-dashboard" class="screen flex-col w-full h-full">
            <header class="p-6 flex items-center justify-between">
                <div>
                    <h1 class="text-2xl font-extrabold text-slate-800">MyDryer X1</h1>
                    <p id="dryer-status-header" class="text-sm font-medium text-green-600">Connected & Ready</p>
                </div>
                <button id="open-settings-btn" class="w-10 h-10 bg-stone-200 rounded-full flex items-center justify-center text-xl hover:bg-stone-300 transition-colors">⚙</button>
            </header>
            <main class="flex-1 flex flex-col items-center justify-center p-6 -mt-8">
                <div class="chart-container">
                    <canvas id="time-remaining-chart"></canvas>
                    <div id="timer-display" class="absolute inset-0 flex flex-col items-center justify-center text-center pointer-events-none">
                        <span id="time-remaining-text" class="text-5xl font-bold text-slate-800">0:00</span>
                        <span id="timer-label" class="text-sm font-medium text-stone-500">Time Remaining</span>
                    </div>
                </div>
            </main>
            <footer class="p-6 bg-stone-100 rounded-t-3xl">
                <div class="grid grid-cols-2 gap-4 text-center mb-6">
                    <div>
                        <p class="text-xs text-stone-500">Temperature</p>
                        <p id="temp-display" class="font-bold text-lg">60°C</p>
                    </div>
                    <div>
                        <p class="text-xs text-stone-500">Duration</p>
                        <p id="duration-display" class="font-bold text-lg">45 min</p>
                    </div>
                </div>
                <button id="power-btn" class="w-full font-bold py-4 px-4 rounded-2xl transition-all duration-300 ease-in-out transform hover:scale-105 bg-cyan-500 text-white">Turn On Dryer</button>
            </footer>
        </div>

    </div>

    <!-- Settings Modal -->
    <div id="settings-modal" class="fixed inset-0 z-50 items-center justify-center hidden modal-bg">
        <div class="bg-white rounded-2xl shadow-lg w-11/12 max-w-sm p-6 modal-content scale-95 opacity-0">
            <h3 class="text-xl font-bold mb-6 text-center">Dryer Settings</h3>
            
            <div class="mb-6">
                <label for="temp-slider" class="block font-medium mb-2">Temperature: <span id="temp-value">60</span>°C</label>
                <input id="temp-slider" type="range" min="30" max="60" value="60" class="w-full h-2 bg-stone-200 rounded-lg appearance-none cursor-pointer">
            </div>

            <div class="mb-8">
                <label class="block font-medium mb-2">Timer (minutes)</label>
                <div class="flex items-center justify-center space-x-4">
                    <button id="timer-minus" class="w-12 h-12 bg-stone-200 text-2xl font-bold rounded-full hover:bg-stone-300 transition-colors">-</button>
                    <span id="timer-value" class="text-3xl font-bold w-20 text-center">45</span>
                    <button id="timer-plus" class="w-12 h-12 bg-stone-200 text-2xl font-bold rounded-full hover:bg-stone-300 transition-colors">+</button>
                </div>
            </div>

            <div class="flex space-x-4 mb-4">
                <button id="cancel-settings-btn" class="w-full bg-stone-200 text-stone-800 font-bold py-3 px-4 rounded-xl hover:bg-stone-300 transition-colors">Cancel</button>
                <button id="save-settings-btn" class="w-full bg-slate-800 text-white font-bold py-3 px-4 rounded-xl hover:bg-slate-700 transition-colors">Save</button>
            </div>
            
            <!-- <button id="get-fabric-advice-btn" class="w-full bg-purple-600 text-white font-bold py-3 px-4 rounded-xl hover:bg-purple-700 transition-colors mt-2">✨ Get Fabric Care Advice ✨</button> -->
        </div>
    </div>

    <!-- Fabric Advice Input Modal -->
    <div id="fabric-input-modal" class="fixed inset-0 z-50 items-center justify-center hidden modal-bg">
        <div class="bg-white rounded-2xl shadow-lg w-11/12 max-w-sm p-6 modal-content scale-95 opacity-0">
            <h3 class="text-xl font-bold mb-6 text-center">What fabric are you drying?</h3>
            <input type="text" id="fabric-input" placeholder="e.g., Cotton, Silk, Denim" class="w-full p-3 border border-stone-300 rounded-lg mb-4 focus:outline-none focus:ring-2 focus:ring-cyan-500">
            <div class="flex space-x-4">
                <button id="cancel-fabric-input-btn" class="w-full bg-stone-200 text-stone-800 font-bold py-3 px-4 rounded-xl hover:bg-stone-300 transition-colors">Cancel</button>
                <button id="submit-fabric-input-btn" class="w-full bg-purple-600 text-white font-bold py-3 px-4 rounded-xl hover:bg-purple-700 transition-colors">Get Advice</button>
            </div>
        </div>
    </div>

    <!-- Advice Display Modal -->
    <div id="advice-display-modal" class="fixed inset-0 z-50 items-center justify-center hidden modal-bg">
        <div class="bg-white rounded-2xl shadow-lg w-11/12 max-w-md p-6 modal-content scale-95 opacity-0">
            <h3 class="text-xl font-bold mb-4 text-center">✨ Fabric Care Advice ✨</h3>
            <div id="advice-content" class="text-stone-700 text-sm leading-relaxed mb-6 bg-stone-100 p-4 rounded-lg overflow-y-auto max-h-64">
                <div class="w-10 h-10 border-4 border-t-4 border-t-purple-500 border-stone-200 rounded-full animate-spin mx-auto my-8"></div>
                <p class="text-center text-stone-500">Generating advice...</p>
            </div>
            <button id="close-advice-btn" class="w-full bg-slate-800 text-white font-bold py-3 px-4 rounded-xl hover:bg-slate-700 transition-colors">Close</button>
        </div>
    </div>

<script>
document.addEventListener('DOMContentLoaded', () => {
    
    // Register Service Worker
    if ('serviceWorker' in navigator) {
        navigator.serviceWorker.register('/LoneRangeGamer/service-worker.js')
            .then(reg => console.log('Service Worker registered:', reg))
            .catch(err => console.error('Service Worker registration failed:', err));
    }

    // Request Notification Permission
    if ('Notification' in window) {
        Notification.requestPermission().then(permission => {
            console.log('Notification permission:', permission);
        }).catch(err => {
            console.error('Error requesting notification permission:', err);
        });
    }
    
    const screens = {
        splash: document.getElementById('screen-splash'),
        bluetooth: document.getElementById('screen-bluetooth'),
        dashboard: document.getElementById('screen-dashboard')
    };

    const bluetoothViews = {
        initial: document.getElementById('bluetooth-initial-view'),
        scan: document.getElementById('scan-btn'),
        scanView: document.getElementById('bluetooth-scan-view'),
        connecting: document.getElementById('bluetooth-connecting-view'),
        devicesList: document.getElementById('devices-list')
    };
    
    const settingsModal = {
        container: document.getElementById('settings-modal'),
        content: document.querySelector('#settings-modal .modal-content'),
        tempSlider: document.getElementById('temp-slider'),
        tempValue: document.getElementById('temp-value'),
        timerValue: document.getElementById('timer-value'),
        timerMinus: document.getElementById('timer-minus'),
        timerPlus: document.getElementById('timer-plus'),
        saveBtn: document.getElementById('save-settings-btn'),
        cancelBtn: document.getElementById('cancel-settings-btn'),
        getFabricAdviceBtn: document.getElementById('get-fabric-advice-btn'),
    };

    const fabricInputModal = {
        container: document.getElementById('fabric-input-modal'),
        content: document.querySelector('#fabric-input-modal .modal-content'),
        fabricInput: document.getElementById('fabric-input'),
        cancelBtn: document.getElementById('cancel-fabric-input-btn'),
        submitBtn: document.getElementById('submit-fabric-input-btn'),
    };

    const adviceDisplayModal = {
        container: document.getElementById('advice-display-modal'),
        content: document.querySelector('#advice-display-modal .modal-content'),
        adviceContent: document.getElementById('advice-content'),
        closeBtn: document.getElementById('close-advice-btn'),
    };
    
    const dashboardElements = {
        openSettingsBtn: document.getElementById('open-settings-btn'),
        powerBtn: document.getElementById('power-btn'),
        dryerStatusHeader: document.getElementById('dryer-status-header'),
        tempDisplay: document.getElementById('temp-display'),
        durationDisplay: document.getElementById('duration-display'),
        timeRemainingText: document.getElementById('time-remaining-text'),
        timerLabel: document.getElementById('timer-label')
    };

    let timeRemainingChart;
    let timerInterval;

    const appState = {
        currentScreen: 'splash',
        temperature: 60,
        duration: 45,
        isDrying: false,
        timeRemaining: 0,
        totalDuration: 45 * 60,
    };

    function navigateTo(screenName) {
        Object.values(screens).forEach(screen => screen.classList.remove('active'));
        if (screens[screenName]) {
            screens[screenName].classList.add('active');
            appState.currentScreen = screenName;
        }
    }
    
    function formatTime(seconds) {
        if (seconds < 0) seconds = 0;
        const m = Math.floor(seconds / 60);
        const s = seconds % 60;
        return `${m}:${s < 10 ? '0' : ''}${s}`;
    }

    function updateDashboardDisplays() {
        dashboardElements.tempDisplay.textContent = `${appState.temperature}°C`;
        dashboardElements.durationDisplay.textContent = `${appState.duration} min`;
        appState.totalDuration = appState.duration * 60;
        if (!appState.isDrying) {
             appState.timeRemaining = appState.totalDuration;
             dashboardElements.timeRemainingText.textContent = formatTime(appState.timeRemaining);
             updateChart(appState.timeRemaining, appState.totalDuration);
        }
    }

    function initChart() {
        const ctx = document.getElementById('time-remaining-chart').getContext('2d');
        timeRemainingChart = new Chart(ctx, {
            type: 'doughnut',
            data: {
                datasets: [{
                    data: [0, 100],
                    backgroundColor: ['#06b6d4', '#e5e7eb'],
                    borderWidth: 0,
                    borderRadius: 20
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                cutout: '80%',
                plugins: {
                    legend: { display: false },
                    tooltip: { enabled: false }
                },
                animation: {
                    duration: 500
                }
            }
        });
        updateDashboardDisplays();
    }
    
    function updateChart(remaining, total) {
        if (!timeRemainingChart) return;
        const progress = total > 0 ? ((total - remaining) / total) * 100 : 0;
        const remainingPercentage = 100 - progress;
        timeRemainingChart.data.datasets[0].data[0] = progress;
        timeRemainingChart.data.datasets[0].data[1] = remainingPercentage;
        timeRemainingChart.update('none'); 
    }

    function showCycleCompletedNotification() {
        if ('Notification' in window && Notification.permission === 'granted') {
            new Notification('Smart Dryer Control', {
                body: 'Cycle Completed!',
                icon: '/LoneRangeGamer/icons/icon-192x192.png'
            });
        } else if (Notification.permission !== 'denied') {
            Notification.requestPermission().then(permission => {
                if (permission === 'granted') {
                    new Notification('Smart Dryer Control', {
                        body: 'Cycle Completed!',
                        icon: '/LoneRangeGamer/icons/icon-192x192.png'
                    });
                }
            });
        }
    }

    function startDryingCycle() {
        if (appState.isDrying) return;
        appState.isDrying = true;
        appState.totalDuration = appState.duration * 60;
        appState.timeRemaining = appState.totalDuration;

        dashboardElements.powerBtn.textContent = 'Turn Off Dryer';
        dashboardElements.powerBtn.classList.remove('bg-cyan-500');
        dashboardElements.powerBtn.classList.add('bg-rose-500');
        dashboardElements.dryerStatusHeader.textContent = 'Drying Cycle Active';
        dashboardElements.dryerStatusHeader.classList.remove('text-green-600');
        dashboardElements.dryerStatusHeader.classList.add('text-amber-600');
        dashboardElements.timerLabel.textContent = "Time Remaining";
        dashboardElements.openSettingsBtn.disabled = true;
        dashboardElements.openSettingsBtn.classList.add('opacity-50');

        timerInterval = setInterval(() => {
            appState.timeRemaining -= 1;
            dashboardElements.timeRemainingText.textContent = formatTime(appState.timeRemaining);
            updateChart(appState.timeRemaining, appState.totalDuration);

            if (appState.timeRemaining <= 0) {
                stopDryingCycle(true);
            }
        }, 1000);
    }
    
    function stopDryingCycle(isFinished = false) {
        clearInterval(timerInterval);
        appState.isDrying = false;
        
        dashboardElements.powerBtn.textContent = 'Turn On Dryer';
        dashboardElements.powerBtn.classList.remove('bg-rose-500');
        dashboardElements.powerBtn.classList.add('bg-cyan-500');
        dashboardElements.dryerStatusHeader.textContent = isFinished ? 'Cycle Complete' : 'Connected & Ready';
        dashboardElements.dryerStatusHeader.classList.add('text-green-600');
        dashboardElements.dryerStatusHeader.classList.remove('text-amber-600');
        dashboardElements.openSettingsBtn.disabled = false;
        dashboardElements.openSettingsBtn.classList.remove('opacity-50');
        
        if (isFinished) {
            dashboardElements.timerLabel.textContent = "Finished!";
            dashboardElements.timeRemainingText.textContent = "Done";
            updateChart(0, 1);
            showCycleCompletedNotification(); // Show notification when cycle completes
        } else {
             updateDashboardDisplays();
        }
    }

    function showModal(modalObj) {
        modalObj.container.classList.remove('hidden');
        modalObj.container.classList.add('flex');
        setTimeout(() => {
            modalObj.container.classList.remove('opacity-0');
            modalObj.content.classList.remove('scale-95', 'opacity-0');
        }, 10);
    }

    function hideModal(modalObj) {
        modalObj.container.classList.add('opacity-0');
        modalObj.content.classList.add('scale-95', 'opacity-0');
        setTimeout(() => {
            modalObj.container.classList.add('hidden');
            modalObj.container.classList.remove('flex');
        }, 300);
    }

    function handleBluetoothConnection() {
        bluetoothViews.initial.classList.add('hidden');
        bluetoothViews.scanView.classList.remove('hidden');

        setTimeout(() => {
            const devices = ['SmartDryer X1', 'Laundry Room Dryer', 'Basement Dryer'];
            bluetoothViews.devicesList.innerHTML = '';
            devices.forEach(device => {
                const btn = document.createElement('button');
                btn.className = 'w-full text-left p-3 bg-stone-100 rounded-lg hover:bg-stone-200 transition-colors';
                btn.textContent = device;
                btn.onclick = () => {
                    bluetoothViews.scanView.classList.add('hidden');
                    bluetoothViews.connecting.classList.remove('hidden');
                    document.getElementById('connecting-device-name').textContent = device;
                    setTimeout(() => {
                        navigateTo('dashboard');
                        initChart();
                    }, 2000);
                };
                bluetoothViews.devicesList.appendChild(btn);
            });
        }, 1500);
    }

    async function getFabricCareAdvice(fabricType) {
        adviceDisplayModal.adviceContent.innerHTML = `
            <div class="w-10 h-10 border-4 border-t-4 border-t-purple-500 border-stone-200 rounded-full animate-spin mx-auto my-8"></div>
            <p class="text-center text-stone-500">Generating advice for ${fabricType}...</p>
        `;
        showModal(adviceDisplayModal);

        const prompt = `Provide concise smart dryer settings and tips for drying ${fabricType}, including recommended temperature (e.g., low, medium, high), duration (e.g., short, medium, long), and any special instructions (e.g., air dry, tumble dry low). Be specific and helpful. Format as a short paragraph.`;
        
        let chatHistory = [];
        chatHistory.push({ role: "user", parts: [{ text: prompt }] });
        const payload = { contents: chatHistory };
        const apiKey = "";
        const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;

        try {
            const response = await fetch(apiUrl, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(payload)
            });
            const result = await response.json();
            if (result.candidates && result.candidates.length > 0 &&
                result.candidates[0].content && result.candidates[0].content.parts &&
                result.candidates[0].content.parts.length > 0) {
                const advice = result.candidates[0].content.parts[0].text;
                adviceDisplayModal.adviceContent.textContent = advice;
            } else {
                adviceDisplayModal.adviceContent.textContent = "Sorry, I couldn't get advice for that fabric. Please try again.";
            }
        } catch (error) {
            adviceDisplayModal.adviceContent.textContent = `An error occurred: ${error.message}. Please check your connection.`;
        }
    }

    // Event Listeners
    setTimeout(() => navigateTo('bluetooth'), 2000);
    
    bluetoothViews.scan.addEventListener('click', handleBluetoothConnection);
    
    dashboardElements.openSettingsBtn.addEventListener('click', () => {
        if (!appState.isDrying) showModal(settingsModal);
    });
    dashboardElements.powerBtn.addEventListener('click', () => {
        appState.isDrying ? stopDryingCycle() : startDryingCycle();
    });

    settingsModal.cancelBtn.addEventListener('click', () => hideModal(settingsModal));
    settingsModal.saveBtn.addEventListener('click', () => {
        appState.temperature = parseInt(settingsModal.tempSlider.value);
        appState.duration = parseInt(settingsModal.timerValue.textContent);
        updateDashboardDisplays();
        hideModal(settingsModal);
    });

    settingsModal.tempSlider.addEventListener('input', (e) => {
        settingsModal.tempValue.textContent = e.target.value;
    });

    settingsModal.timerMinus.addEventListener('click', () => {
        let current = parseInt(settingsModal.timerValue.textContent);
        if (current > 5) {
            settingsModal.timerValue.textContent = current - 5;
        }
    });

    settingsModal.timerPlus.addEventListener('click', () => {
        let current = parseInt(settingsModal.timerValue.textContent);
         if (current < 180) {
            settingsModal.timerValue.textContent = current + 5;
        }
    });

    // LLM Integration Event Listeners
    settingsModal.getFabricAdviceBtn.addEventListener('click', () => {
        hideModal(settingsModal);
        showModal(fabricInputModal);
        fabricInputModal.fabricInput.value = ''; // Clear previous input
    });

    fabricInputModal.cancelBtn.addEventListener('click', () => {
        hideModal(fabricInputModal);
        showModal(settingsModal); // Return to settings modal
    });

    fabricInputModal.submitBtn.addEventListener('click', () => {
        const fabricType = fabricInputModal.fabricInput.value.trim();
        if (fabricType) {
            hideModal(fabricInputModal);
            getFabricCareAdvice(fabricType);
        } else {
            fabricInputModal.fabricInput.placeholder = "Please enter a fabric type!";
            fabricInputModal.fabricInput.classList.add('border-red-500');
        }
    });

    adviceDisplayModal.closeBtn.addEventListener('click', () => {
        hideModal(adviceDisplayModal);
        showModal(settingsModal); // Return to settings modal
    });
});
</script>
</body>
</html>
