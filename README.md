<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DVS Professional Master Portal v3.0 - Dynamic</title>
    <style>
        :root {
            --main: #1a237e;
            --main-light: #3949ab;
            --neg: #b71c1c;
            --neg-light: #ffebee;
            --pos: #1b5e20;
            --pos-light: #e8f5e9;
            --bg: #f5f7fa;
            --gold: #d4af37;
            --shadow: 0 2px 8px rgba(0,0,0,0.1);
            --shadow-lg: 0 5px 20px rgba(0,0,0,0.15);
        }
        
        * { box-sizing: border-box; }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: var(--bg);
            margin: 0;
            padding: 0;
            min-height: 100vh;
        }
        
        .header {
            background: linear-gradient(135deg, var(--main) 0%, var(--main-light) 100%);
            color: white;
            padding: 20px;
            text-align: center;
            box-shadow: var(--shadow);
        }
        
        .header h1 {
            margin: 0 0 5px 0;
            font-size: 1.8em;
        }
        
        .header small {
            opacity: 0.9;
            font-size: 0.9em;
        }
        
        /* Login Section */
        #login-section {
            max-width: 400px;
            margin: 50px auto;
            padding: 30px;
            background: white;
            border-radius: 15px;
            box-shadow: var(--shadow-lg);
        }
        
        #login-section h2 {
            color: var(--main);
            text-align: center;
            margin-bottom: 30px;
        }
        
        .login-logo {
            text-align: center;
            font-size: 4em;
            margin-bottom: 20px;
        }
        
        /* Menu Cards */
        .menu-container {
            padding: 20px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 15px;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .menu-card {
            background: white;
            padding: 25px;
            border-radius: 12px;
            text-align: center;
            box-shadow: var(--shadow);
            cursor: pointer;
            border: 2px solid transparent;
            transition: all 0.3s ease;
        }
        
        .menu-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-lg);
            border-color: var(--main);
        }
        
        .menu-card span {
            font-size: 1.1em;
            font-weight: 500;
        }
        
        .menu-card .icon {
            font-size: 2.5em;
            margin-bottom: 10px;
        }
        
        /* Container Panels */
        .container {
            padding: 20px;
            display: none;
            max-width: 800px;
            margin: 0 auto;
        }
        
        .panel {
            background: white;
            padding: 30px;
            border-radius: 15px;
            box-shadow: var(--shadow-lg);
            margin-top: 20px;
        }
        
        .panel h2, .panel h3 {
            margin-top: 0;
            border-bottom: 3px solid var(--main);
            padding-bottom: 10px;
        }
        
        /* Form Elements */
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            font-size: 0.95em;
            color: #333;
        }
        
        input, select, textarea {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 15px;
            transition: border-color 0.3s;
            font-family: inherit;
        }
        
        input:focus, select:focus, textarea:focus {
            outline: none;
            border-color: var(--main);
        }
        
        textarea {
            resize: vertical;
            min-height: 80px;
        }
        
        /* Buttons */
        .btn {
            width: 100%;
            padding: 15px;
            border: none;
            border-radius: 8px;
            color: white;
            font-weight: bold;
            font-size: 16px;
            cursor: pointer;
            margin-top: 10px;
            transition: all 0.3s;
        }
        
        .btn:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow);
        }
        
        .btn:active {
            transform: translateY(0);
        }
        
        .btn-main { background: var(--main); }
        .btn-main:hover { background: var(--main-light); }
        .btn-neg { background: var(--neg); }
        .btn-neg:hover { background: #c62828; }
        .btn-pos { background: var(--pos); }
        .btn-pos:hover { background: #2e7d32; }
        .btn-danger { background: #d32f2f; }
        .btn-danger:hover { background: #f44336; }
        
        .btn-back {
            width: auto;
            padding: 10px 20px;
            margin-bottom: 15px;
            background: #757575;
        }
        
        .btn-back:hover {
            background: #616161;
        }
        
        .btn-small {
            width: auto;
            padding: 8px 15px;
            font-size: 14px;
            margin: 5px;
        }
        
        /* Report Grid */
        .report-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 15px;
            margin-top: 25px;
        }
        
        .neg-col, .pos-col {
            padding: 20px;
            border-radius: 10px;
            min-height: 200px;
        }
        
        .neg-col {
            background: var(--neg-light);
            border: 2px solid var(--neg);
        }
        
        .pos-col {
            background: var(--pos-light);
            border: 2px solid var(--pos);
        }
        
        .neg-col h4 {
            color: var(--neg);
            margin-top: 0;
        }
        
        .pos-col h4 {
            color: var(--pos);
            margin-top: 0;
        }
        
        .log-entry {
            background: white;
            padding: 12px;
            margin-bottom: 10px;
            border-radius: 6px;
            border-left: 4px solid;
            font-size: 0.9em;
        }
        
        .neg-col .log-entry {
            border-left-color: var(--neg);
        }
        
        .pos-col .log-entry {
            border-left-color: var(--pos);
        }
        
        .total-row {
            font-weight: bold;
            margin-top: 15px;
            padding-top: 15px;
            border-top: 3px solid #333;
            font-size: 1.1em;
        }
        
        /* Alert Messages */
        .alert {
            padding: 15px 20px;
            border-radius: 8px;
            margin-bottom: 20px;
            font-weight: 500;
        }
        
        .alert-success {
            background: var(--pos-light);
            color: var(--pos);
            border: 2px solid var(--pos);
        }
        
        .alert-error {
            background: var(--neg-light);
            color: var(--neg);
            border: 2px solid var(--neg);
        }
        
        .alert-warning {
            background: #fff3e0;
            color: #e65100;
            border: 2px solid #ff9800;
        }
        
        /* Stats Cards */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-bottom: 25px;
        }
        
        .stat-card {
            background: linear-gradient(135deg, var(--main) 0%, var(--main-light) 100%);
            color: white;
            padding: 20px;
            border-radius: 10px;
            text-align: center;
        }
        
        .stat-card h3 {
            margin: 0;
            font-size: 2em;
        }
        
        .stat-card p {
            margin: 5px 0 0 0;
            opacity: 0.9;
        }
        
        /* Warning Box */
        .warning-box {
            background: #fff3e0;
            border: 3px solid #ff9800;
            border-radius: 10px;
            padding: 20px;
            margin: 20px 0;
            text-align: center;
        }
        
        .warning-box h4 {
            color: #e65100;
            margin-top: 0;
        }
        
        /* Config Item */
        .config-item {
            background: #f5f5f5;
            padding: 15px;
            margin: 10px 0;
            border-radius: 8px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-left: 4px solid var(--main);
        }
        
        .config-item-content {
            flex: 1;
        }
        
        .config-item-actions {
            display: flex;
            gap: 10px;
        }
        
        .icon-btn {
            background: none;
            border: none;
            font-size: 1.2em;
            cursor: pointer;
            padding: 5px 10px;
            border-radius: 5px;
            transition: all 0.3s;
        }
        
        .icon-btn:hover {
            background: rgba(0,0,0,0.1);
        }
        
        .edit-btn { color: #1976d2; }
        .delete-btn { color: #d32f2f; }
        
        /* Toggle Switch */
        .toggle-switch {
            position: relative;
            display: inline-block;
            width: 60px;
            height: 34px;
        }
        
        .toggle-switch input {
            opacity: 0;
            width: 0;
            height: 0;
        }
        
        .toggle-slider {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-color: #ccc;
            transition: .4s;
            border-radius: 34px;
        }
        
        .toggle-slider:before {
            position: absolute;
            content: "";
            height: 26px;
            width: 26px;
            left: 4px;
            bottom: 4px;
            background-color: white;
            transition: .4s;
            border-radius: 50%;
        }
        
        input:checked + .toggle-slider {
            background-color: var(--pos);
        }
        
        input:checked + .toggle-slider:before {
            transform: translateX(26px);
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .menu-container {
                grid-template-columns: 1fr;
            }
            
            .report-grid {
                grid-template-columns: 1fr;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
            }
            
            .config-item {
                flex-direction: column;
                align-items: flex-start;
            }
            
            .config-item-actions {
                margin-top: 10px;
            }
        }
        
        /* Loading Spinner */
        .spinner {
            border: 3px solid #f3f3f3;
            border-top: 3px solid var(--main);
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
            margin: 20px auto;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        .hidden {
            display: none !important;
        }
        
        .badge {
            display: inline-block;
            padding: 4px 12px;
            border-radius: 12px;
            font-size: 0.85em;
            font-weight: 600;
            margin-left: 10px;
        }
        
        .badge-admin {
            background: #ff9800;
            color: white;
        }
        
        .section-divider {
            border-top: 2px solid #e0e0e0;
            margin: 30px 0;
            padding-top: 20px;
        }
    </style>
</head>
<body>

<!-- Login Section -->
<div id="login-section">
    <div class="login-logo">🏫</div>
    <h2 id="loginTitle">DVS MASTER LOGIN</h2>
    <div class="form-group">
        <label>User ID</label>
        <input type="text" id="uID" placeholder="Enter your User ID" autocomplete="username">
    </div>
    <div class="form-group">
        <label>Password</label>
        <input type="password" id="uPass" placeholder="Enter your Password" autocomplete="current-password">
    </div>
    <button class="btn btn-main" onclick="doLogin()">Login to Portal</button>
</div>

<!-- Portal Section -->
<div id="portal-section" style="display:none;">
    <div class="header" id="mainHeader">
        <h1 id="headerTitle">🏫 DERAWALA VIDYA SANKUL</h1>
        <small id="userDisplay"></small>
    </div>

    <!-- Main Menu -->
    <div id="main-menu" class="menu-container">
        <div class="menu-card admin-only" onclick="showPanel('tab-t-reg')" style="display:none;">
            <div class="icon">👨‍🏫</div>
            <span>Teacher Registration</span>
        </div>
        <div class="menu-card admin-only" onclick="showPanel('tab-s-reg')" style="display:none;">
            <div class="icon">🎓</div>
            <span>Student Registration</span>
        </div>
        <div class="menu-card" onclick="showPanel('tab-neg')">
            <div class="icon">⚠️</div>
            <span>Negative BMC</span>
        </div>
        <div class="menu-card" onclick="showPanel('tab-pos')">
            <div class="icon">🏆</div>
            <span>Positive BMC</span>
        </div>
        <div class="menu-card admin-only" onclick="showPanel('tab-ana')" style="display:none;">
            <div class="icon">📊</div>
            <span>Analytics & Reports</span>
        </div>
        <div class="menu-card admin-only" onclick="showPanel('tab-manage')" style="display:none;">
            <div class="icon">⚙️</div>
            <span>Manage Records</span>
        </div>
        <div class="menu-card admin-only" onclick="showPanel('tab-config')" style="display:none;">
            <div class="icon">🔧</div>
            <span>System Configuration<span class="badge badge-admin">ADMIN</span></span>
        </div>
        <div class="menu-card" onclick="showPanel('tab-security')">
            <div class="icon">🔐</div>
            <span>Security Settings</span>
        </div>
        <div class="menu-card" onclick="doLogout()" style="background:#fff0f0;">
            <div class="icon" style="color:red;">🚪</div>
            <span style="color:red;">Logout</span>
        </div>
    </div>

    <!-- System Configuration Panel -->
    <div id="tab-config" class="container">
        <button class="btn btn-back" onclick="showMenu()">← Back to Menu</button>
        <div class="panel" style="border-top: 5px solid #ff9800;">
            <h2 style="color:#ff9800;">🔧 System Configuration <span class="badge badge-admin">ADMIN ONLY</span></h2>
            
            <!-- School Branding -->
            <div class="section-divider">
                <h3>🏫 School Branding</h3>
                <div class="form-group">
                    <label>School Name</label>
                    <input type="text" id="cfgSchoolName" placeholder="Enter school name">
                </div>
                <div class="form-group">
                    <label>School Motto</label>
                    <input type="text" id="cfgMotto" placeholder="Enter school motto">
                </div>
                <div class="form-group">
                    <label>Primary Color</label>
                    <input type="color" id="cfgPrimaryColor">
                </div>
                <div class="form-group">
                    <label>Secondary Color</label>
                    <input type="color" id="cfgSecondaryColor">
                </div>
                <button class="btn btn-main" onclick="saveBranding()">💾 Save Branding</button>
            </div>
            
            <!-- Class Management -->
            <div class="section-divider">
                <h3>📚 Class Management</h3>
                <div id="classList"></div>
                <div class="form-group">
                    <label>Add New Class</label>
                    <input type="text" id="newClassName" placeholder="e.g., Class 11-A">
                </div>
                <button class="btn btn-main" onclick="addClass()">➕ Add Class</button>
            </div>
            
            <!-- Behavior Issues Library -->
            <div class="section-divider">
                <h3>📋 Behavior Issues Library</h3>
                <div id="issuesLibrary"></div>
                <div class="form-group">
                    <label>Issue Grade</label>
                    <select id="newIssueGrade">
                        <option value="">-- Select Grade --</option>
                        <option value="Grade 1">Grade 1 (Minor)</option>
                        <option value="Grade 2">Grade 2 (Moderate)</option>
                        <option value="Grade 3">Grade 3 (Serious)</option>
                        <option value="Grade 4">Grade 4 (Severe)</option>
                        <option value="Grade 5">Grade 5 (Critical)</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Issue ID</label>
                    <input type="text" id="newIssueID" placeholder="e.g., ISS-0098">
                </div>
                <div class="form-group">
                    <label>Issue Description</label>
                    <input type="text" id="newIssueDesc" placeholder="e.g., Uniform violation">
                </div>
                <button class="btn btn-main" onclick="addIssue()">➕ Add Issue</button>
            </div>
            
            <!-- Feature Toggles -->
            <div class="section-divider">
                <h3>⚙️ Feature Toggles</h3>
                <div class="config-item">
                    <div class="config-item-content">
                        <strong>Parent Notifications</strong>
                        <p style="margin:5px 0 0 0; color:#666; font-size:0.9em;">Allow teachers to send notifications to parents</p>
                    </div>
                    <label class="toggle-switch">
                        <input type="checkbox" id="toggleParentNotif" onchange="saveFeatureToggle('parentNotifications', this.checked)">
                        <span class="toggle-slider"></span>
                    </label>
                </div>
                <div class="config-item">
                    <div class="config-item-content">
                        <strong>Student Self-View</strong>
                        <p style="margin:5px 0 0 0; color:#666; font-size:0.9em;">Allow students to view their own records</p>
                    </div>
                    <label class="toggle-switch">
                        <input type="checkbox" id="toggleStudentView" onchange="saveFeatureToggle('studentSelfView', this.checked)">
                        <span class="toggle-slider"></span>
                    </label>
                </div>
                <div class="config-item">
                    <div class="config-item-content">
                        <strong>Auto-Archive Old Records</strong>
                        <p style="margin:5px 0 0 0; color:#666; font-size:0.9em;">Automatically archive records older than 1 year</p>
                    </div>
                    <label class="toggle-switch">
                        <input type="checkbox" id="toggleAutoArchive" onchange="saveFeatureToggle('autoArchive', this.checked)">
                        <span class="toggle-slider"></span>
                    </label>
                </div>
            <
