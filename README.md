# Advocate's pocket world
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advocate Office Manager - Staff Management & Communication</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary-color: #1e3c72;
            --secondary-color: #2a5298;
            --accent-color: #4a90e2;
            --success-color: #28a745;
            --warning-color: #ffc107;
            --danger-color: #dc3545;
            --light-bg: #f4f7fc;
            --dark-text: #333;
            --border-radius: 10px;
            --box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: var(--light-bg);
            color: var(--dark-text);
        }

        /* Header Styles */
        .header {
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: white;
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
        }

        .logo h1 {
            font-size: 1.8rem;
            margin-bottom: 0.2rem;
        }

        .logo p {
            font-size: 0.9rem;
            opacity: 0.9;
        }

        .user-info {
            display: flex;
            align-items: center;
            gap: 1.5rem;
        }

        .user-badge {
            background: rgba(255,255,255,0.2);
            padding: 0.5rem 1rem;
            border-radius: 50px;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .user-badge i {
            font-size: 1.2rem;
        }

        .logout-btn {
            background: rgba(255,255,255,0.1);
            border: 1px solid rgba(255,255,255,0.3);
            color: white;
            padding: 0.5rem 1.5rem;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .logout-btn:hover {
            background: rgba(255,255,255,0.2);
            transform: translateY(-2px);
        }

        /* Main Container */
        .main-container {
            display: flex;
            margin-top: 80px;
            min-height: calc(100vh - 80px);
        }

        /* Sidebar */
        .sidebar {
            width: 280px;
            background: white;
            box-shadow: var(--box-shadow);
            padding: 2rem 0;
            position: fixed;
            height: calc(100vh - 80px);
            overflow-y: auto;
        }

        .sidebar-menu {
            list-style: none;
        }

        .sidebar-menu li {
            padding: 0.8rem 2rem;
            margin: 0.5rem 0;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 1rem;
            color: #555;
        }

        .sidebar-menu li:hover {
            background: rgba(74, 144, 226, 0.1);
            color: var(--accent-color);
            border-left: 4px solid var(--accent-color);
        }

        .sidebar-menu li.active {
            background: rgba(74, 144, 226, 0.15);
            color: var(--accent-color);
            border-left: 4px solid var(--accent-color);
            font-weight: 600;
        }

        .sidebar-menu li i {
            width: 24px;
            font-size: 1.2rem;
        }

        /* Content Area */
        .content {
            flex: 1;
            margin-left: 280px;
            padding: 2rem;
        }

        /* Dashboard Cards */
        .dashboard-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin-bottom: 2rem;
        }

        .card {
            background: white;
            border-radius: var(--border-radius);
            padding: 1.5rem;
            box-shadow: var(--box-shadow);
            transition: transform 0.3s;
        }

        .card:hover {
            transform: translateY(-5px);
        }

        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1rem;
        }

        .card-header i {
            font-size: 2rem;
            color: var(--accent-color);
        }

        .card-value {
            font-size: 2rem;
            font-weight: bold;
            color: var(--primary-color);
        }

        .card-label {
            color: #666;
            font-size: 0.9rem;
        }

        /* Section Styles */
        .section {
            display: none;
            background: white;
            border-radius: var(--border-radius);
            padding: 2rem;
            box-shadow: var(--box-shadow);
        }

        .section.active {
            display: block;
        }

        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
        }

        .section-header h2 {
            color: var(--primary-color);
            font-size: 1.8rem;
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: white;
            border: none;
            padding: 0.8rem 1.5rem;
            border-radius: 50px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            transition: all 0.3s;
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }

        /* Table Styles */
        .table-container {
            overflow-x: auto;
        }

        table {
            width: 100%;
            border-collapse: collapse;
        }

        th {
            background: var(--light-bg);
            color: var(--primary-color);
            font-weight: 600;
            padding: 1rem;
            text-align: left;
        }

        td {
            padding: 1rem;
            border-bottom: 1px solid #eee;
        }

        tr:hover {
            background: #f9f9f9;
        }

        .status-badge {
            padding: 0.3rem 0.8rem;
            border-radius: 50px;
            font-size: 0.85rem;
            font-weight: 600;
        }

        .status-active {
            background: #d4edda;
            color: #155724;
        }

        .status-inactive {
            background: #f8d7da;
            color: #721c24;
        }

        .status-pending {
            background: #fff3cd;
            color: #856404;
        }

        .action-icons {
            display: flex;
            gap: 1rem;
        }

        .action-icons i {
            cursor: pointer;
            color: #666;
            transition: color 0.3s;
        }

        .action-icons i:hover {
            color: var(--accent-color);
        }

        /* Chat Area */
        .chat-container {
            display: flex;
            height: 600px;
            background: white;
            border-radius: var(--border-radius);
            overflow: hidden;
        }

        .chat-sidebar {
            width: 300px;
            border-right: 1px solid #eee;
            background: #f9f9f9;
        }

        .chat-search {
            padding: 1rem;
            border-bottom: 1px solid #eee;
        }

        .chat-search input {
            width: 100%;
            padding: 0.8rem;
            border: 1px solid #ddd;
            border-radius: 50px;
            outline: none;
        }

        .chat-users {
            overflow-y: auto;
            height: calc(100% - 70px);
        }

        .chat-user {
            display: flex;
            align-items: center;
            gap: 1rem;
            padding: 1rem;
            cursor: pointer;
            transition: background 0.3s;
            border-bottom: 1px solid #eee;
        }

        .chat-user:hover {
            background: #f0f0f0;
        }

        .chat-user.active {
            background: rgba(74, 144, 226, 0.1);
        }

        .user-avatar {
            width: 40px;
            height: 40px;
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
        }

        .user-info h4 {
            font-size: 1rem;
            margin-bottom: 0.2rem;
        }

        .user-info p {
            font-size: 0.8rem;
            color: #666;
        }

        .chat-main {
            flex: 1;
            display: flex;
            flex-direction: column;
        }

        .chat-header {
            padding: 1rem;
            border-bottom: 1px solid #eee;
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .chat-messages {
            flex: 1;
            padding: 1rem;
            overflow-y: auto;
            background: #fafafa;
        }

        .message {
            display: flex;
            align-items: flex-start;
            gap: 1rem;
            margin-bottom: 1rem;
        }

        .message.sent {
            flex-direction: row-reverse;
        }

        .message-content {
            max-width: 70%;
            padding: 0.8rem 1rem;
            border-radius: 15px;
            background: white;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
        }

        .message.sent .message-content {
            background: var(--accent-color);
            color: white;
        }

        .message-time {
            font-size: 0.7rem;
            color: #999;
            margin-top: 0.3rem;
        }

        .chat-input {
            padding: 1rem;
            border-top: 1px solid #eee;
            display: flex;
            gap: 1rem;
        }

        .chat-input input {
            flex: 1;
            padding: 0.8rem;
            border: 1px solid #ddd;
            border-radius: 50px;
            outline: none;
        }

        .chat-input button {
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: white;
            border: none;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            cursor: pointer;
            transition: all 0.3s;
        }

        .chat-input button:hover {
            transform: scale(1.1);
        }

        /* Records Section */
        .records-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1.5rem;
            margin-top: 1.5rem;
        }

        .record-card {
            background: white;
            border: 1px solid #eee;
            border-radius: var(--border-radius);
            padding: 1.5rem;
        }

        .record-card h3 {
            color: var(--primary-color);
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .record-list {
            list-style: none;
        }

        .record-list li {
            padding: 0.8rem 0;
            border-bottom: 1px solid #eee;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .record-list li:last-child {
            border-bottom: none;
        }

        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 2000;
            justify-content: center;
            align-items: center;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: white;
            border-radius: var(--border-radius);
            padding: 2rem;
            width: 90%;
            max-width: 500px;
            max-height: 90vh;
            overflow-y: auto;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
        }

        .modal-header h3 {
            color: var(--primary-color);
        }

        .close-modal {
            font-size: 2rem;
            cursor: pointer;
            color: #666;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            color: #555;
            font-weight: 600;
        }

        .form-group input,
        .form-group select,
        .form-group textarea {
            width: 100%;
            padding: 0.8rem;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-family: inherit;
        }

        .form-group textarea {
            height: 100px;
            resize: vertical;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .sidebar {
                transform: translateX(-100%);
                transition: transform 0.3s;
                z-index: 1500;
            }

            .sidebar.active {
                transform: translateX(0);
            }

            .content {
                margin-left: 0;
            }

            .chat-container {
                flex-direction: column;
                height: auto;
            }

            .chat-sidebar {
                width: 100%;
                height: 300px;
            }
        }
    </style>
    <!-- Font Awesome for icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
</head>
<body>
    <!-- Header -->
    <header class="header">
        <div class="logo">
            <h1>Advocate Office Manager</h1>
            <p>Staff Management & Communication Portal</p>
        </div>
        <div class="user-info">
            <div class="user-badge">
                <i class="fas fa-user-circle"></i>
                <span>Advocate Sarah Johnson</span>
            </div>
            <button class="logout-btn" onclick="logout()">
                <i class="fas fa-sign-out-alt"></i> Logout
            </button>
        </div>
    </header>

    <!-- Main Container -->
    <div class="main-container">
        <!-- Sidebar -->
        <aside class="sidebar" id="sidebar">
            <ul class="sidebar-menu">
                <li class="active" onclick="showSection('dashboard')">
                    <i class="fas fa-home"></i>
                    <span>Dashboard</span>
                </li>
                <li onclick="showSection('staff')">
                    <i class="fas fa-users"></i>
                    <span>Staff Management</span>
                </li>
                <li onclick="showSection('chat')">
                    <i class="fas fa-comments"></i>
                    <span>Chat</span>
                </li>
                <li onclick="showSection('records')">
                    <i class="fas fa-folder"></i>
                    <span>Records</span>
                </li>
                <li onclick="showSection('tasks')">
                    <i class="fas fa-tasks"></i>
                    <span>Tasks</span>
                </li>
                <li onclick="showSection('calendar')">
                    <i class="fas fa-calendar"></i>
                    <span>Calendar</span>
                </li>
                <li onclick="showSection('reports')">
                    <i class="fas fa-chart-bar"></i>
                    <span>Reports</span>
                </li>
                <li onclick="showSection('settings')">
                    <i class="fas fa-cog"></i>
                    <span>Settings</span>
                </li>
            </ul>
        </aside>

        <!-- Content Area -->
        <div class="content" id="content">
            <!-- Dashboard Section -->
            <section id="dashboard" class="section active">
                <div class="section-header">
                    <h2>Dashboard</h2>
                    <div class="date-display">
                        <i class="fas fa-calendar-alt"></i>
                        <span id="currentDate"></span>
                    </div>
                </div>

                <div class="dashboard-cards">
                    <div class="card">
                        <div class="card-header">
                            <i class="fas fa-users"></i>
                            <span class="card-value">12</span>
                        </div>
                        <div class="card-label">Total Staff</div>
                    </div>
                    <div class="card">
                        <div class="card-header">
                            <i class="fas fa-clock"></i>
                            <span class="card-value">8</span>
                        </div>
                        <div class="card-label">Currently Active</div>
                    </div>
                    <div class="card">
                        <div class="card-header">
                            <i class="fas fa-calendar-check"></i>
                            <span class="card-value">24</span>
                        </div>
                        <div class="card-label">Pending Tasks</div>
                    </div>
                    <div class="card">
                        <div class="card-header">
                            <i class="fas fa-comment"></i>
                            <span class="card-value">156</span>
                        </div>
                        <div class="card-label">New Messages</div>
                    </div>
                </div>

                <div class="dashboard-cards">
                    <div class="card">
                        <div class="card-header">
                            <i class="fas fa-folder-open"></i>
                            <span class="card-value">45</span>
                        </div>
                        <div class="card-label">Active Cases</div>
                    </div>
                    <div class="card">
                        <div class="card-header">
                            <i class="fas fa-hourglass-half"></i>
                            <span class="card-value">12</span>
                        </div>
                        <div class="card-label">Upcoming Deadlines</div>
                    </div>
                    <div class="card">
                        <div class="card-header">
                            <i class="fas fa-file-pdf"></i>
                            <span class="card-value">89</span>
                        </div>
                        <div class="card-label">Documents</div>
                    </div>
                    <div class="card">
                        <div class="card-header">
                            <i class="fas fa-video"></i>
                            <span class="card-value">3</span>
                        </div>
                        <div class="card-label">Meetings Today</div>
                    </div>
                </div>
            </section>

            <!-- Staff Management Section -->
            <section id="staff" class="section">
                <div class="section-header">
                    <h2>Staff Management</h2>
                    <button class="btn-primary" onclick="openModal('addStaffModal')">
                        <i class="fas fa-plus"></i> Add Staff
                    </button>
                </div>

                <div class="table-container">
                    <table>
                        <thead>
                            <tr>
                                <th>Name</th>
                                <th>Role</th>
                                <th>Department</th>
                                <th>Email</th>
                                <th>Phone</th>
                                <th>Status</th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody id="staffTableBody">
                            <!-- Staff data will be populated here -->
                        </tbody>
                    </table>
                </div>
            </section>

            <!-- Chat Section -->
            <section id="chat" class="section">
                <div class="section-header">
                    <h2>Chat</h2>
                </div>

                <div class="chat-container">
                    <div class="chat-sidebar">
                        <div class="chat-search">
                            <input type="text" placeholder="Search staff..." id="chatSearch">
                        </div>
                        <div class="chat-users" id="chatUsers">
                            <!-- Chat users will be populated here -->
                        </div>
                    </div>
                    <div class="chat-main">
                        <div class="chat-header" id="chatHeader">
                            <div class="user-avatar">JS</div>
                            <div>
                                <h4>John Smith</h4>
                                <p>Online</p>
                            </div>
                        </div>
                        <div class="chat-messages" id="chatMessages">
                            <!-- Messages will be displayed here -->
                        </div>
                        <div class="chat-input">
                            <input type="text" placeholder="Type your message..." id="messageInput">
                            <button onclick="sendMessage()">
                                <i class="fas fa-paper-plane"></i>
                            </button>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Records Section -->
            <section id="records" class="section">
                <div class="section-header">
                    <h2>Records</h2>
                    <button class="btn-primary" onclick="openModal('addRecordModal')">
                        <i class="fas fa-plus"></i> Add Record
                    </button>
                </div>

                <div class="records-grid">
                    <div class="record-card">
                        <h3><i class="fas fa-file-contract"></i> Case Documents</h3>
                        <ul class="record-list" id="caseDocuments">
                            <!-- Case documents will be listed here -->
                        </ul>
                    </div>
                    <div class="record-card">
                        <h3><i class="fas fa-clock"></i> Attendance Records</h3>
                        <ul class="record-list" id="attendanceRecords">
                            <!-- Attendance records will be listed here -->
                        </ul>
                    </div>
                    <div class="record-card">
                        <h3><i class="fas fa-money-bill"></i> Payroll Records</h3>
                        <ul class="record-list" id="payrollRecords">
                            <!-- Payroll records will be listed here -->
                        </ul>
                    </div>
                    <div class="record-card">
                        <h3><i class="fas fa-calendar-alt"></i> Leave Requests</h3>
                        <ul class="record-list" id="leaveRequests">
                            <!-- Leave requests will be listed here -->
                        </ul>
                    </div>
                </div>
            </section>

            <!-- Tasks Section -->
            <section id="tasks" class="section">
                <div class="section-header">
                    <h2>Tasks</h2>
                    <button class="btn-primary" onclick="openModal('addTaskModal')">
                        <i class="fas fa-plus"></i> Add Task
                    </button>
                </div>

                <div class="table-container">
                    <table>
                        <thead>
                            <tr>
                                <th>Task</th>
                                <th>Assigned To</th>
                                <th>Priority</th>
                                <th>Due Date</th>
                                <th>Status</th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody id="tasksTableBody">
                            <!-- Tasks will be populated here -->
                        </tbody>
                    </table>
                </div>
            </section>

            <!-- Calendar Section -->
            <section id="calendar" class="section">
                <div class="section-header">
                    <h2>Calendar</h2>
                </div>

                <div class="calendar-container">
                    <!-- Simple calendar representation -->
                    <div class="dashboard-cards">
                        <div class="card">
                            <h3>Today's Schedule</h3>
                            <ul class="record-list" id="todaySchedule">
                                <!-- Today's schedule will be listed here -->
                            </ul>
                        </div>
                        <div class="card">
                            <h3>Upcoming Events</h3>
                            <ul class="record-list" id="upcomingEvents">
                                <!-- Upcoming events will be listed here -->
                            </ul>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Reports Section -->
            <section id="reports" class="section">
                <div class="section-header">
                    <h2>Reports</h2>
                    <button class="btn-primary" onclick="generateReport()">
                        <i class="fas fa-download"></i> Generate Report
                    </button>
                </div>

                <div class="dashboard-cards">
                    <div class="card">
                        <h3>Staff Performance</h3>
                        <canvas id="performanceChart"></canvas>
                    </div>
                    <div class="card">
                        <h3>Case Load Distribution</h3>
                        <canvas id="caseLoadChart"></canvas>
                    </div>
                </div>
            </section>

            <!-- Settings Section -->
            <section id="settings" class="section">
                <div class="section-header">
                    <h2>Settings</h2>
                </div>

                <div class="settings-container">
                    <div class="card">
                        <h3>Profile Settings</h3>
                        <div class="form-group">
                            <label>Name</label>
                            <input type="text" value="Sarah Johnson" disabled>
                        </div>
                        <div class="form-group">
                            <label>Email</label>
                            <input type="email" value="sarah.johnson@advocateoffice.com" disabled>
                        </div>
                        <div class="form-group">
                            <label>Phone</label>
                            <input type="tel" value="+1 234 567 8900" disabled>
                        </div>
                        <button class="btn-primary" onclick="editProfile()">Edit Profile</button>
                    </div>
                    
                    <div class="card">
                        <h3>Notification Preferences</h3>
                        <div class="form-group">
                            <label>
                                <input type="checkbox" checked> Email Notifications
                            </label>
                        </div>
                        <div class="form-group">
                            <label>
                                <input type="checkbox" checked> SMS Notifications
                            </label>
                        </div>
                        <div class="form-group">
                            <label>
                                <input type="checkbox"> Desktop Notifications
                            </label>
                        </div>
                    </div>
                </div>
            </section>
        </div>
    </div>

    <!-- Add Staff Modal -->
    <div class="modal" id="addStaffModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3>Add New Staff</h3>
                <span class="close-modal" onclick="closeModal('addStaffModal')">&times;</span>
            </div>
            <form id="addStaffForm" onsubmit="addStaff(event)">
                <div class="form-group">
                    <label>Full Name</label>
                    <input type="text" required>
                </div>
                <div class="form-group">
                    <label>Role</label>
                    <select required>
                        <option value="">Select Role</option>
                        <option>Paralegal</option>
                        <option>Legal Assistant</option>
                        <option>Office Manager</option>
                        <option>Receptionist</option>
                        <option>Intern</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Department</label>
                    <select required>
                        <option value="">Select Department</option>
                        <option>Criminal Law</option>
                        <option>Civil Law</option>
                        <option>Corporate Law</option>
                        <option>Family Law</option>
                        <option>Administration</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Email</label>
                    <input type="email" required>
                </div>
                <div class="form-group">
                    <label>Phone</label>
                    <input type="tel" required>
                </div>
                <div class="form-group">
                    <label>Join Date</label>
                    <input type="date" required>
                </div>
                <button type="submit" class="btn-primary">Add Staff</button>
            </form>
        </div>
    </div>

    <!-- Add Record Modal -->
    <div class="modal" id="addRecordModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3>Add New Record</h3>
                <span class="close-modal" onclick="closeModal('addRecordModal')">&times;</span>
            </div>
            <form id="addRecordForm" onsubmit="addRecord(event)">
                <div class="form-group">
                    <label>Record Type</label>
                    <select required>
                        <option value="">Select Type</option>
                        <option>Case Document</option>
                        <option>Attendance</option>
                        <option>Payroll</option>
                        <option>Leave Request</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Title</label>
                    <input type="text" required>
                </div>
                <div class="form-group">
                    <label>Description</label>
                    <textarea required></textarea>
                </div>
                <div class="form-group">
                    <label>Date</label>
                    <input type="date" required>
                </div>
                <div class="form-group">
                    <label>Attach File</label>
                    <input type="file">
                </div>
                <button type="submit" class="btn-primary">Add Record</button>
            </form>
        </div>
    </div>

    <!-- Add Task Modal -->
    <div class="modal" id="addTaskModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3>Add New Task</h3>
                <span class="close-modal" onclick="closeModal('addTaskModal')">&times;</span>
            </div>
            <form id="addTaskForm" onsubmit="addTask(event)">
                <div class="form-group">
                    <label>Task Title</label>
                    <input type="text" required>
                </div>
                <div class="form-group">
                    <label>Assign To</label>
                    <select required>
                        <option value="">Select Staff</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Priority</label>
                    <select required>
                        <option>High</option>
                        <option>Medium</option>
                        <option>Low</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Due Date</label>
                    <input type="date" required>
                </div>
                <div class="form-group">
                    <label>Description</label>
                    <textarea required></textarea>
                </div>
                <button type="submit" class="btn-primary">Add Task</button>
            </form>
        </div>
    </div>

    <script>
        // Sample data
        let staffData = [
            { name: 'John Smith', role: 'Paralegal', department: 'Criminal Law', email: 'john.smith@email.com', phone: '+1 234-567-8901', status: 'Active' },
            { name: 'Emma Wilson', role: 'Legal Assistant', department: 'Civil Law', email: 'emma.w@email.com', phone: '+1 234-567-8902', status: 'Active' },
            { name: 'Michael Brown', role: 'Office Manager', department: 'Administration', email: 'michael.b@email.com', phone: '+1 234-567-8903', status: 'Active' },
            { name: 'Lisa Davis', role: 'Paralegal', department: 'Corporate Law', email: 'lisa.d@email.com', phone: '+1 234-567-8904', status: 'On Leave' },
            { name: 'Robert Taylor', role: 'Receptionist', department: 'Administration', email: 'robert.t@email.com', phone: '+1 234-567-8905', status: 'Active' }
        ];

        let messages = [
            { user: 'John Smith', message: 'Good morning, I\'ve completed the research for the Smith case.', time: '09:30 AM', sent: false },
            { user: 'You', message: 'Great work! Please send me the summary.', time: '09:32 AM', sent: true },
            { user: 'John Smith', message: 'Sure, I\'ll email it right away.', time: '09:33 AM', sent: false }
        ];

        let tasks = [
            { task: 'Prepare case brief for Johnson vs State', assigned: 'John Smith', priority: 'High', dueDate: '2024-01-25', status: 'In Progress' },
            { task: 'Review contract documents', assigned: 'Emma Wilson', priority: 'Medium', dueDate: '2024-01-26', status: 'Pending' },
            { task: 'Schedule client meeting', assigned: 'Lisa Davis', priority: 'Low', dueDate: '2024-01-27', status: 'Completed' },
            { task: 'File court documents', assigned: 'Michael Brown', priority: 'High', dueDate: '2024-01-24', status: 'In Progress' }
        ];

        let records = {
            caseDocuments: [
                'Smith vs State - Case Brief.pdf',
                'Johnson Contract - Draft.docx',
                'Williams Estate - Will.pdf'
            ],
            attendance: [
                'John Smith - Present',
                'Emma Wilson - Present',
                'Michael Brown - Late',
                'Lisa Davis - Leave'
            ],
            payroll: [
                'January 2024 - Processed',
                'December 2023 - Paid',
                'November 2023 - Paid'
            ],
            leaveRequests: [
                'Emma Wilson - Jan 25-27 (Pending)',
                'Robert Taylor - Feb 1-5 (Approved)',
                'Lisa Davis - Jan 28-30 (Pending)'
            ]
        };

        // Initialize the page
        document.addEventListener('DOMContentLoaded', function() {
            updateDate();
            populateStaffTable();
            populateChatUsers();
            displayMessages();
            populateTasks();
            populateRecords();
            populateSchedule();
            populateEvents();
        });

        function updateDate() {
            const dateElement = document.getElementById('currentDate');
            const options = { weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' };
            dateElement.textContent = new Date().toLocaleDateString('en-US', options);
        }

        function showSection(sectionId) {
            // Hide all sections
            document.querySelectorAll('.section').forEach(section => {
                section.classList.remove('active');
            });

            // Show selected section
            document.getElementById(sectionId).classList.add('active');

            // Update active menu item
            document.querySelectorAll('.sidebar-menu li').forEach(item => {
                item.classList.remove('active');
            });
            event.currentTarget.classList.add('active');
        }

        function populateStaffTable() {
            const tbody = document.getElementById('staffTableBody');
            tbody.innerHTML = '';

            staffData.forEach(staff => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${staff.name}</td>
                    <td>${staff.role}</td>
                    <td>${staff.department}</td>
                    <td>${staff.email}</td>
                    <td>${staff.phone}</td>
                    <td><span class="status-badge status-${staff.status.toLowerCase().replace(' ', '')}">${staff.status}</span></td>
                    <td class="action-icons">
                        <i class="fas fa-edit" onclick="editStaff('${staff.name}')" title="Edit"></i>
                        <i class="fas fa-trash" onclick="deleteStaff('${staff.name}')" title="Delete"></i>
                        <i class="fas fa-envelope" onclick="messageStaff('${staff.name}')" title="Message"></i>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function populateChatUsers() {
            const chatUsers = document.getElementById('chatUsers');
            chatUsers.innerHTML = '';

            staffData.forEach(staff => {
                if (staff.status === 'Active') {
                    const userDiv = document.createElement('div');
                    userDiv.className = 'chat-user';
                    userDiv.onclick = () => selectChatUser(staff.name);
                    userDiv.innerHTML = `
                        <div class="user-avatar">${staff.name.split(' ').map(n => n[0]).join('')}</div>
                        <div class="user-info">
                            <h4>${staff.name}</h4>
                            <p>${staff.role}</p>
                        </div>
                    `;
                    chatUsers.appendChild(userDiv);
                }
            });
        }

        function displayMessages() {
            const messagesContainer = document.getElementById('chatMessages');
            messagesContainer.innerHTML = '';

            messages.forEach(msg => {
                const messageDiv = document.createElement('div');
                messageDiv.className = `message ${msg.sent ? 'sent' : ''}`;
                messageDiv.innerHTML = `
                    <div class="user-avatar">${msg.user.split(' ').map(n => n[0]).join('')}</div>
                    <div class="message-content">
                        <p>${msg.message}</p>
                        <div class="message-time">${msg.time}</div>
                    </div>
                `;
                messagesContainer.appendChild(messageDiv);
            });

            // Scroll to bottom
            messagesContainer.scrollTop = messagesContainer.scrollHeight;
        }

        function selectChatUser(userName) {
            document.querySelectorAll('.chat-user').forEach(user => {
                user.classList.remove('active');
            });
            event.currentTarget.classList.add('active');
            
            document.getElementById('chatHeader').innerHTML = `
                <div class="user-avatar">${userName.split(' ').map(n => n[0]).join('')}</div>
                <div>
                    <h4>${userName}</h4>
                    <p>Online</p>
                </div>
            `;
        }

        function sendMessage() {
            const input = document.getElementById('messageInput');
            const message = input.value.trim();

            if (message) {
                messages.push({
                    user: 'You',
                    message: message,
                    time: new Date().toLocaleTimeString('en-US', { hour: '2-digit', minute: '2-digit' }),
                    sent: true
                });
                
                displayMessages();
                input.value = '';
            }
        }

        function populateTasks() {
            const tbody = document.getElementById('tasksTableBody');
            tbody.innerHTML = '';

            tasks.forEach(task => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${task.task}</td>
                    <td>${task.assigned}</td>
                    <td><span class="status-badge status-${task.priority.toLowerCase()}">${task.priority}</span></td>
                    <td>${task.dueDate}</td>
                    <td><span class="status-badge status-${task.status.toLowerCase().replace(' ', '')}">${task.status}</span></td>
                    <td class="action-icons">
                        <i class="fas fa-check" onclick="completeTask('${task.task}')" title="Complete"></i>
                        <i class="fas fa-edit" onclick="editTask('${task.task}')" title="Edit"></i>
                    </td>
                `;
                tbody.appendChild(row);
            });
        }

        function populateRecords() {
            // Case Documents
            const caseDocs = document.getElementById('caseDocuments');
            caseDocs.innerHTML = records.caseDocuments.map(doc => 
                `<li>${doc} <i class="fas fa-download" onclick="downloadFile('${doc}')"></i></li>`
            ).join('');

            // Attendance Records
            const attendance = document.getElementById('attendanceRecords');
            attendance.innerHTML = records.attendance.map(record => 
                `<li>${record}</li>`
            ).join('');

            // Payroll Records
            const payroll = document.getElementById('payrollRecords');
            payroll.innerHTML = records.payroll.map(record => 
                `<li>${record}</li>`
            ).join('');

            // Leave Requests
            const leave = document.getElementById('leaveRequests');
            leave.innerHTML = records.leaveRequests.map(request => 
                `<li>${request} <i class="fas fa-check-circle" style="color: green;" onclick="approveLeave('${request}')"></i></li>`
            ).join('');
        }

        function populateSchedule() {
            const schedule = document.getElementById('todaySchedule');
            schedule.innerHTML = `
                <li>10:00 AM - Client Meeting (Room 101)</li>
                <li>11:30 AM - Staff Meeting (Conference Room)</li>
                <li>2:00 PM - Court Hearing (Room 205)</li>
                <li>4:00 PM - Document Review</li>
            `;
        }

        function populateEvents() {
            const events = document.getElementById('upcomingEvents');
            events.innerHTML = `
                <li>Jan 25 - Case Filing Deadline</li>
                <li>Jan 26 - Staff Training Session</li>
                <li>Jan 27 - Client Deposition</li>
                <li>Jan 30 - Monthly Review Meeting</li>
            `;
        }

        // Modal functions
        function openModal(modalId) {
            document.getElementById(modalId).classList.add('active');
        }

        function closeModal(modalId) {
            document.getElementById(modalId).classList.remove('active');
        }

        // Form submissions
        function addStaff(event) {
            event.preventDefault();
            alert('Staff added successfully!');
            closeModal('addStaffModal');
            // In real app, you would add the data to your array and refresh the table
        }

        function addRecord(event) {
            event.preventDefault();
            alert('Record added successfully!');
            closeModal('addRecordModal');
        }

        function addTask(event) {
            event.preventDefault();
            alert('Task added successfully!');
            closeModal('addTaskModal');
        }

        // Action functions
        function editStaff(name) {
            alert(`Edit staff: ${name}`);
        }

        function deleteStaff(name) {
            if (confirm(`Are you sure you want to delete ${name}?`)) {
                alert(`Staff ${name} deleted`);
                // In real app, remove from array and refresh table
            }
        }

        function messageStaff(name) {
            showSection('chat');
            alert(`Opening chat with ${name}`);
        }

        function completeTask(task) {
            alert(`Task "${task}" marked as complete`);
        }

        function editTask(task) {
            alert(`Edit task: ${task}`);
        }

        function downloadFile(file) {
            alert(`Downloading ${file}`);
        }

        function approveLeave(request) {
            alert(`Leave request ${request} approved`);
        }

        function generateReport() {
            alert('Generating report...');
        }

        function editProfile() {
            alert('Edit profile functionality');
        }

        function logout() {
            if (confirm('Are you sure you want to logout?')) {
                alert('Logged out successfully');
                // In real app, redirect to login page
            }
        }

        // Search functionality
        document.getElementById('chatSearch')?.addEventListener('input', function(e) {
            const searchTerm = e.target.value.toLowerCase();
            const users = document.querySelectorAll('.chat-user');
            
            users.forEach(user => {
                const name = user.querySelector('h4').textContent.toLowerCase();
                if (name.includes(searchTerm)) {
                    user.style.display = 'flex';
                } else {
                    user.style.display = 'none';
                }
            });
        });

        // Keyboard shortcut for sending messages
        document.getElementById('messageInput')?.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                sendMessage();
            }