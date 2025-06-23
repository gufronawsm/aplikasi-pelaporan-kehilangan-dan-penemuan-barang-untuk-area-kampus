<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lost & Found Campus</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
            overflow: hidden;
        }

        .header {
            background: linear-gradient(135deg, #2c3e50, #34495e);
            color: white;
            padding: 30px;
            text-align: center;
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            font-weight: 700;
        }

        .header p {
            font-size: 1.1em;
            opacity: 0.9;
        }

        .nav-tabs {
            display: flex;
            background: #f8f9fa;
            border-bottom: 3px solid #e9ecef;
        }

        .nav-tab {
            flex: 1;
            padding: 20px;
            background: none;
            border: none;
            font-size: 1.1em;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            color: #6c757d;
        }

        .nav-tab.active {
            background: white;
            color: #2c3e50;
            border-bottom: 3px solid #3498db;
        }

        .nav-tab:hover {
            background: #e9ecef;
        }

        .content {
            padding: 30px;
        }

        .form-section {
            display: none;
            animation: fadeIn 0.5s ease-in;
        }

        .form-section.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .form-group {
            margin-bottom: 25px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #2c3e50;
            font-size: 1.1em;
        }

        .form-group input,
        .form-group select,
        .form-group textarea {
            width: 100%;
            padding: 15px;
            border: 2px solid #e9ecef;
            border-radius: 12px;
            font-size: 1em;
            transition: all 0.3s ease;
            background: #f8f9fa;
        }

        .form-group input:focus,
        .form-group select:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: #3498db;
            background: white;
            box-shadow: 0 0 0 3px rgba(52, 152, 219, 0.1);
        }

        .form-group textarea {
            min-height: 120px;
            resize: vertical;
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
        }

        .btn {
            background: linear-gradient(135deg, #3498db, #2980b9);
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 1.1em;
            font-weight: 600;
            border-radius: 12px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(52, 152, 219, 0.3);
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(52, 152, 219, 0.4);
        }

        .btn-success {
            background: linear-gradient(135deg, #27ae60, #229954);
            box-shadow: 0 4px 15px rgba(39, 174, 96, 0.3);
        }

        .btn-success:hover {
            box-shadow: 0 6px 20px rgba(39, 174, 96, 0.4);
        }

        .reports-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 25px;
            margin-top: 20px;
        }

        .report-card {
            background: white;
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
            border-left: 5px solid #3498db;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .report-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(90deg, #3498db, #2980b9);
        }

        .report-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 35px rgba(0, 0, 0, 0.15);
        }

        .report-card.found {
            border-left-color: #27ae60;
        }

        .report-card.found::before {
            background: linear-gradient(90deg, #27ae60, #229954);
        }

        .report-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }

        .report-type {
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 0.9em;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .report-type.lost {
            background: #ffebee;
            color: #c62828;
        }

        .report-type.found {
            background: #e8f5e8;
            color: #2e7d32;
        }

        .report-date {
            color: #6c757d;
            font-size: 0.9em;
        }

        .report-item {
            font-size: 1.3em;
            font-weight: 700;
            color: #2c3e50;
            margin-bottom: 10px;
        }

        .report-details {
            color: #6c757d;
            line-height: 1.6;
        }

        .report-location {
            background: #f8f9fa;
            padding: 10px 15px;
            border-radius: 8px;
            margin: 15px 0;
            font-weight: 600;
            color: #495057;
        }

        .report-contact {
            margin-top: 15px;
            padding-top: 15px;
            border-top: 1px solid #e9ecef;
            font-size: 0.95em;
            color: #6c757d;
        }

        .match-indicator {
            position: absolute;
            top: 15px;
            right: 15px;
            background: #ff9800;
            color: white;
            padding: 5px 10px;
            border-radius: 15px;
            font-size: 0.8em;
            font-weight: 600;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }

        .search-bar {
            margin-bottom: 25px;
        }

        .search-bar input {
            padding: 15px 20px;
            border: 2px solid #e9ecef;
            border-radius: 25px;
            font-size: 1em;
            width: 100%;
            background: #f8f9fa;
        }

        .search-bar input:focus {
            outline: none;
            border-color: #3498db;
            background: white;
        }

        .stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .stat-card {
            background: white;
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            border-top: 4px solid #3498db;
        }

        .stat-number {
            font-size: 2.5em;
            font-weight: 700;
            color: #2c3e50;
            margin-bottom: 5px;
        }

        .stat-label {
            color: #6c757d;
            font-weight: 600;
        }

        @media (max-width: 768px) {
            .form-row {
                grid-template-columns: 1fr;
            }
            
            .nav-tabs {
                flex-direction: column;
            }
            
            .header h1 {
                font-size: 2em;
            }
            
            .reports-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🎓 Lost & Found Campus</h1>
            <p>Sistem Pelaporan Kehilangan dan Penemuan Barang Area Kampus</p>
        </div>

        <div class="nav-tabs">
            <button class="nav-tab active" onclick="showSection('lapor-hilang')">📋 Lapor Hilang</button>
            <button class="nav-tab" onclick="showSection('lapor-temukan')">🔍 Lapor Temukan</button>
            <button class="nav-tab" onclick="showSection('daftar-laporan')">📊 Daftar Laporan</button>
        </div>

        <div class="content">
            <!-- Form Lapor Hilang -->
            <div id="lapor-hilang" class="form-section active">
                <h2 style="margin-bottom: 25px; color: #2c3e50;">Laporkan Barang Hilang</h2>
                <form id="lostItemForm">
                    <div class="form-row">
                        <div class="form-group">
                            <label for="lostItemName">Nama Barang</label>
                            <input type="text" id="lostItemName" required placeholder="Contoh: Dompet kulit coklat">
                        </div>
                        <div class="form-group">
                            <label for="lostCategory">Kategori</label>
                            <select id="lostCategory" required>
                                <option value="">Pilih Kategori</option>
                                <option value="elektronik">Elektronik</option>
                                <option value="dokumen">Dokumen</option>
                                <option value="aksesoris">Aksesoris</option>
                                <option value="tas">Tas</option>
                                <option value="kunci">Kunci</option>
                                <option value="lainnya">Lainnya</option>
                            </select>
                        </div>
                    </div>
                    
                    <div class="form-group">
                        <label for="lostDescription">Deskripsi Detail</label>
                        <textarea id="lostDescription" required placeholder="Deskripsikan barang secara detail (warna, merek, ukuran, ciri khusus, dll)"></textarea>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="lostLocation">Lokasi Terakhir</label>
                            <input type="text" id="lostLocation" required placeholder="Contoh: Ruang Kuliah A101, Perpustakaan Lt.2">
                        </div>
                        <div class="form-group">
                            <label for="lostDate">Tanggal Hilang</label>
                            <input type="date" id="lostDate" required>
                        </div>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="lostReporterName">Nama Pelapor</label>
                            <input type="text" id="lostReporterName" required placeholder="Nama lengkap">
                        </div>
                        <div class="form-group">
                            <label for="lostReporterContact">Kontak (WA/Email)</label>
                            <input type="text" id="lostReporterContact" required placeholder="08123456789 atau email@example.com">
                        </div>
                    </div>
                    
                    <button type="submit" class="btn">📋 Submit Laporan Hilang</button>
                </form>
            </div>

            <!-- Form Lapor Temukan -->
            <div id="lapor-temukan" class="form-section">
                <h2 style="margin-bottom: 25px; color: #2c3e50;">Laporkan Barang Ditemukan</h2>
                <form id="foundItemForm">
                    <div class="form-row">
                        <div class="form-group">
                            <label for="foundItemName">Nama Barang</label>
                            <input type="text" id="foundItemName" required placeholder="Contoh: Dompet kulit coklat">
                        </div>
                        <div class="form-group">
                            <label for="foundCategory">Kategori</label>
                            <select id="foundCategory" required>
                                <option value="">Pilih Kategori</option>
                                <option value="elektronik">Elektronik</option>
                                <option value="dokumen">Dokumen</option>
                                <option value="aksesoris">Aksesoris</option>
                                <option value="tas">Tas</option>
                                <option value="kunci">Kunci</option>
                                <option value="lainnya">Lainnya</option>
                            </select>
                        </div>
                    </div>
                    
                    <div class="form-group">
                        <label for="foundDescription">Deskripsi Detail</label>
                        <textarea id="foundDescription" required placeholder="Deskripsikan barang yang ditemukan secara detail"></textarea>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="foundLocation">Lokasi Ditemukan</label>
                            <input type="text" id="foundLocation" required placeholder="Contoh: Kantin Lt.1, Parkiran Motor">
                        </div>
                        <div class="form-group">
                            <label for="foundDate">Tanggal Ditemukan</label>
                            <input type="date" id="foundDate" required>
                        </div>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="foundReporterName">Nama Penemu</label>
                            <input type="text" id="foundReporterName" required placeholder="Nama lengkap">
                        </div>
                        <div class="form-group">
                            <label for="foundReporterContact">Kontak (WA/Email)</label>
                            <input type="text" id="foundReporterContact" required placeholder="08123456789 atau email@example.com">
                        </div>
                    </div>
                    
                    <div class="form-group">
                        <label for="foundCurrentLocation">Barang Disimpan Di</label>
                        <input type="text" id="foundCurrentLocation" required placeholder="Contoh: Ruang Kemahasiswaan, Security Post">
                    </div>
                    
                    <button type="submit" class="btn btn-success">🔍 Submit Laporan Temukan</button>
                </form>
            </div>

            <!-- Daftar Laporan -->
            <div id="daftar-laporan" class="form-section">
                <h2 style="margin-bottom: 25px; color: #2c3e50;">Daftar Laporan</h2>
                
                <div class="stats">
                    <div class="stat-card">
                        <div class="stat-number" id="totalLost">0</div>
                        <div class="stat-label">Barang Hilang</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="totalFound">0</div>
                        <div class="stat-label">Barang Ditemukan</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-number" id="totalMatches">0</div>
                        <div class="stat-label">Kemungkinan Match</div>
                    </div>
                </div>

                <div class="search-bar">
                    <input type="text" id="searchInput" placeholder="🔍 Cari berdasarkan nama barang, lokasi, atau deskripsi...">
                </div>
                
                <div id="reportsContainer" class="reports-grid">
                    <!-- Reports will be dynamically added here -->
                </div>
            </div>
        </div>
    </div>

    <script>
        // Data storage
        let lostItems = [];
        let foundItems = [];
        let currentFilter = '';

        // Initialize
        document.addEventListener('DOMContentLoaded', function() {
            loadSampleData();
            updateStats();
            displayReports();
            
            // Set today as default date
            const today = new Date().toISOString().split('T')[0];
            document.getElementById('lostDate').value = today;
            document.getElementById('foundDate').value = today;
        });

        // Load sample data
        function loadSampleData() {
            lostItems = [
                {
                    id: 1,
                    name: "iPhone 13 Pro",
                    category: "elektronik",
                    description: "iPhone 13 Pro warna biru, case clear dengan sticker universitas",
                    location: "Perpustakaan Lt.2",
                    date: "2025-06-20",
                    reporterName: "Ahmad Rizki",
                    reporterContact: "081234567890",
                    type: "lost"
                },
                {
                    id: 2,
                    name: "Dompet Kulit Coklat",
                    category: "aksesoris",
                    description: "Dompet kulit coklat merek eiger, berisi KTP dan kartu mahasiswa",
                    location: "Kantin Lt.1",
                    date: "2025-06-21",
                    reporterName: "Sari Indah",
                    reporterContact: "sari@email.com",
                    type: "lost"
                }
            ];

            foundItems = [
                {
                    id: 1,
                    name: "Kunci Motor Honda",
                    category: "kunci",
                    description: "Kunci motor Honda dengan gantungan kunci kartun doraemon",
                    location: "Parkiran Motor Blok A",
                    date: "2025-06-22",
                    reporterName: "Budi Santoso",
                    reporterContact: "081345678901",
                    currentLocation: "Security Post",
                    type: "found"
                },
                {
                    id: 2,
                    name: "Smartwatch Hitam",
                    category: "elektronik",
                    description: "Smartwatch warna hitam, merek xiaomi, tali silicon",
                    location: "Lab Komputer",
                    date: "2025-06-23",
                    reporterName: "Lisa Maharani",
                    reporterContact: "lisa@email.com",
                    currentLocation: "Ruang Admin Fakultas",
                    type: "found"
                }
            ];
        }

        // Show section
        function showSection(sectionId) {
            // Hide all sections
            document.querySelectorAll('.form-section').forEach(section => {
                section.classList.remove('active');
            });
            
            // Remove active class from all tabs
            document.querySelectorAll('.nav-tab').forEach(tab => {
                tab.classList.remove('active');
            });
            
            // Show selected section
            document.getElementById(sectionId).classList.add('active');
            
            // Add active class to clicked tab
            event.target.classList.add('active');
            
            // Update reports if viewing reports section
            if (sectionId === 'daftar-laporan') {
                updateStats();
                displayReports();
            }
        }

        // Handle lost item form submission
        document.getElementById('lostItemForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const newItem = {
                id: Date.now(),
                name: document.getElementById('lostItemName').value,
                category: document.getElementById('lostCategory').value,
                description: document.getElementById('lostDescription').value,
                location: document.getElementById('lostLocation').value,
                date: document.getElementById('lostDate').value,
                reporterName: document.getElementById('lostReporterName').value,
                reporterContact: document.getElementById('lostReporterContact').value,
                type: 'lost'
            };
            
            lostItems.push(newItem);
            
            // Reset form
            this.reset();
            const today = new Date().toISOString().split('T')[0];
            document.getElementById('lostDate').value = today;
            
            alert('✅ Laporan barang hilang berhasil disubmit!');
            
            // Check for potential matches
            checkForMatches();
        });

        // Handle found item form submission
        document.getElementById('foundItemForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const newItem = {
                id: Date.now(),
                name: document.getElementById('foundItemName').value,
                category: document.getElementById('foundCategory').value,
                description: document.getElementById('foundDescription').value,
                location: document.getElementById('foundLocation').value,
                date: document.getElementById('foundDate').value,
                reporterName: document.getElementById('foundReporterName').value,
                reporterContact: document.getElementById('foundReporterContact').value,
                currentLocation: document.getElementById('foundCurrentLocation').value,
                type: 'found'
            };
            
            foundItems.push(newItem);
            
            // Reset form
            this.reset();
            const today = new Date().toISOString().split('T')[0];
            document.getElementById('foundDate').value = today;
            
            alert('✅ Laporan barang ditemukan berhasil disubmit!');
            
            // Check for potential matches
            checkForMatches();
        });

        // Search functionality
        document.getElementById('searchInput').addEventListener('input', function(e) {
            currentFilter = e.target.value.toLowerCase();
            displayReports();
        });

        // Display reports
        function displayReports() {
            const container = document.getElementById('reportsContainer');
            const allItems = [...lostItems, ...foundItems];
            
            // Filter items based on search
            const filteredItems = allItems.filter(item => {
                if (!currentFilter) return true;
                
                return item.name.toLowerCase().includes(currentFilter) ||
                       item.description.toLowerCase().includes(currentFilter) ||
                       item.location.toLowerCase().includes(currentFilter) ||
                       item.category.toLowerCase().includes(currentFilter);
            });
            
            // Sort by date (newest first)
            filteredItems.sort((a, b) => new Date(b.date) - new Date(a.date));
            
            container.innerHTML = '';
            
            if (filteredItems.length === 0) {
                container.innerHTML = '<p style="text-align: center; color: #6c757d; font-size: 1.2em; margin: 50px 0;">Tidak ada laporan yang ditemukan.</p>';
                return;
            }
            
            filteredItems.forEach(item => {
                const card = createReportCard(item);
                container.appendChild(card);
            });
        }

        // Create report card
        function createReportCard(item) {
            const card = document.createElement('div');
            card.className = `report-card ${item.type}`;
            
            // Check for potential matches
            const hasMatch = checkItemMatch(item);
            
            card.innerHTML = `
                ${hasMatch ? '<div class="match-indicator">🎯 Kemungkinan Match!</div>' : ''}
                <div class="report-header">
                    <span class="report-type ${item.type}">${item.type === 'lost' ? 'Hilang' : 'Ditemukan'}</span>
                    <span class="report-date">${formatDate(item.date)}</span>
                </div>
                <div class="report-item">${item.name}</div>
                <div class="report-details">${item.description}</div>
                <div class="report-location">
                    📍 ${item.type === 'lost' ? 'Terakhir dilihat' : 'Ditemukan'}: ${item.location}
                    ${item.currentLocation ? `<br>📦 Disimpan di: ${item.currentLocation}` : ''}
                </div>
                <div class="report-contact">
                    👤 ${item.reporterName}<br>
                    📞 ${item.reporterContact}
                </div>
            `;
            
            return card;
        }

        // Check for potential matches
        function checkItemMatch(item) {
            const oppositeItems = item.type === 'lost' ? foundItems : lostItems;
            
            return oppositeItems.some(opposite => {
                const nameMatch = item.name.toLowerCase().includes(opposite.name.toLowerCase()) || 
                                 opposite.name.toLowerCase().includes(item.name.toLowerCase());
                const categoryMatch = item.category === opposite.category;
                const descriptionMatch = item.description.toLowerCase().includes(opposite.description.toLowerCase()) ||
                                       opposite.description.toLowerCase().includes(item.description.toLowerCase());
                
                return nameMatch || (categoryMatch && descriptionMatch);
            });
        }

        // Check for matches and show alert
        function checkForMatches() {
            let matchCount = 0;
            
            lostItems.forEach(lost => {
                if (checkItemMatch(lost)) matchCount++;
            });
            
            if (matchCount > 0) {
                setTimeout(() => {
                    alert(`🎯 Ditemukan ${matchCount} kemungkinan match! Silakan cek di tab "Daftar Laporan".`);
                }, 1000);
            }
        }

        // Update statistics
        function updateStats() {
            document.getElementById('totalLost').textContent = lostItems.length;
            document.getElementById('totalFound').textContent = foundItems.length;
            
            let matches = 0;
            [...lostItems, ...foundItems].forEach(item => {
                if (checkItemMatch(item)) matches++;
            });
            
            document.getElementById('totalMatches').textContent = Math.floor(matches / 2);
        }

        // Format date
        function formatDate(dateString) {
            const date = new Date(dateString);
            const options = { 
                weekday: 'long', 
                year: 'numeric', 
                month: 'long', 
                day: 'numeric' 
            };
            return date.toLocaleDateString('id-ID', options);
        }
    </script>
</body>
</html>
