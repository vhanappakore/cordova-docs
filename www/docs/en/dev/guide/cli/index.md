<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AC Repair Service - Admin Panel</title>
    <style>
        :root {
            --primary: #3498db;
            --secondary: #2c3e50;
            --success: #2ecc71;
            --warning: #f39c12;
            --danger: #e74c3c;
            --light: #ecf0f1;
            --dark: #34495e;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
        }
        
        .container {
            display: flex;
            min-height: 100vh;
        }
        
        /* Sidebar Styles */
        .sidebar {
            width: 250px;
            background: var(--secondary);
            color: white;
            transition: all 0.3s;
        }
        
        .sidebar-header {
            padding: 20px;
            background: var(--primary);
            text-align: center;
        }
        
        .sidebar-menu {
            padding: 15px 0;
        }
        
        .sidebar-menu ul {
            list-style: none;
        }
        
        .sidebar-menu li {
            padding: 12px 20px;
            border-bottom: 1px solid rgba(255,255,255,0.1);
            cursor: pointer;
            transition: all 0.2s;
        }
        
        .sidebar-menu li:hover {
            background: rgba(255,255,255,0.1);
        }
        
        .sidebar-menu li.active {
            background: var(--primary);
            border-left: 4px solid white;
        }
        
        .sidebar-menu i {
            margin-right: 10px;
        }
        
        /* Main Content Styles */
        .main-content {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
        }
        
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            padding-bottom: 15px;
            border-bottom: 1px solid #ddd;
        }
        
        .page-title {
            font-size: 24px;
            font-weight: 600;
            color: var(--secondary);
        }
        
        .user-info {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: var(--primary);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
        }
        
        /* Dashboard Cards */
        .dashboard-cards {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .card {
            background: white;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            transition: transform 0.3s;
        }
        
        .card:hover {
            transform: translateY(-5px);
        }
        
        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .card-title {
            font-size: 16px;
            color: #7f8c8d;
        }
        
        .card-icon {
            width: 40px;
            height: 40px;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
        }
        
        .card-value {
            font-size: 28px;
            font-weight: 700;
            margin-bottom: 5px;
        }
        
        .card-footer {
            font-size: 14px;
            color: #7f8c8d;
        }
        
        /* Table Styles */
        .table-container {
            background: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            margin-bottom: 30px;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        th, td {
            padding: 15px;
            text-align: left;
            border-bottom: 1px solid #eee;
        }
        
        th {
            background: var(--light);
            font-weight: 600;
            color: var(--dark);
        }
        
        tr:hover {
            background: #f9f9f9;
        }
        
        .status {
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
        }
        
        .status-pending {
            background: #fff3cd;
            color: #856404;
        }
        
        .status-completed {
            background: #d1ecf1;
            color: #0c5460;
        }
        
        .status-in-progress {
            background: #d4edda;
            color: #155724;
        }
        
        .btn {
            padding: 8px 15px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.2s;
        }
        
        .btn-primary {
            background: var(--primary);
            color: white;
        }
        
        .btn-success {
            background: var(--success);
            color: white;
        }
        
        .btn-danger {
            background: var(--danger);
            color: white;
        }
        
        .btn-sm {
            padding: 5px 10px;
            font-size: 12px;
        }
        
        /* Form Styles */
        .form-container {
            background: white;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            margin-bottom: 30px;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--dark);
        }
        
        input, select, textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 14px;
        }
        
        .form-row {
            display: flex;
            gap: 20px;
        }
        
        .form-row .form-group {
            flex: 1;
        }
        
        /* Tabs */
        .tabs {
            display: flex;
            border-bottom: 1px solid #ddd;
            margin-bottom: 20px;
        }
        
        .tab {
            padding: 10px 20px;
            cursor: pointer;
            border-bottom: 3px solid transparent;
        }
        
        .tab.active {
            border-bottom: 3px solid var(--primary);
            color: var(--primary);
            font-weight: 600;
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .container {
                flex-direction: column;
            }
            
            .sidebar {
                width: 100%;
                height: auto;
            }
            
            .dashboard-cards {
                grid-template-columns: 1fr;
            }
            
            .form-row {
                flex-direction: column;
                gap: 0;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Sidebar -->
        <div class="sidebar">
            <div class="sidebar-header">
                <h2>AC Repair Admin</h2>
            </div>
            <div class="sidebar-menu">
                <ul>
                    <li class="active" onclick="showTab('dashboard')">
                        <i>📊</i> Dashboard
                    </li>
                    <li onclick="showTab('service-requests')">
                        <i>🔧</i> Service Requests
                    </li>
                    <li onclick="showTab('technicians')">
                        <i>👨‍🔧</i> Technicians
                    </li>
                    <li onclick="showTab('customers')">
                        <i>👥</i> Customers
                    </li>
                    <li onclick="showTab('inventory')">
                        <i>📦</i> Inventory
                    </li>
                    <li onclick="showTab('reports')">
                        <i>📈</i> Reports
                    </li>
                    <li onclick="showTab('settings')">
                        <i>⚙️</i> Settings
                    </li>
                </ul>
            </div>
        </div>
        
        <!-- Main Content -->
        <div class="main-content">
            <div class="header">
                <h1 class="page-title" id="page-title">Dashboard</h1>
                <div class="user-info">
                    <div class="avatar">AD</div>
                    <span>Admin User</span>
                </div>
            </div>
            
            <!-- Dashboard Tab -->
            <div id="dashboard" class="tab-content active">
                <div class="dashboard-cards">
                    <div class="card">
                        <div class="card-header">
                            <h3 class="card-title">Total Requests</h3>
                            <div class="card-icon" style="background: var(--primary);">📋</div>
                        </div>
                        <div class="card-value">142</div>
                        <div class="card-footer">+12% from last month</div>
                    </div>
                    
                    <div class="card">
                        <div class="card-header">
                            <h3 class="card-title">Pending Requests</h3>
                            <div class="card-icon" style="background: var(--warning);">⏳</div>
                        </div>
                        <div class="card-value">24</div>
                        <div class="card-footer">5 urgent requests</div>
                    </div>
                    
                    <div class="card">
                        <div class="card-header">
                            <h3 class="card-title">Completed This Month</h3>
                            <div class="card-icon" style="background: var(--success);">✅</div>
                        </div>
                        <div class="card-value">98</div>
                        <div class="card-footer">+8% from last month</div>
                    </div>
                    
                    <div class="card">
                        <div class="card-header">
                            <h3 class="card-title">Revenue</h3>
                            <div class="card-icon" style="background: var(--danger);">💰</div>
                        </div>
                        <div class="card-value">$12,540</div>
                        <div class="card-footer">+15% from last month</div>
                    </div>
                </div>
                
                <div class="table-container">
                    <h3 style="padding: 15px;">Recent Service Requests</h3>
                    <table>
                        <thead>
                            <tr>
                                <th>ID</th>
                                <th>Customer</th>
                                <th>Service Type</th>
                                <th>Date</th>
                                <th>Technician</th>
                                <th>Status</th>
                                <th>Action</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>#ACR-1024</td>
                                <td>John Smith</td>
                                <td>AC Repair</td>
                                <td>12 May 2023</td>
                                <td>Mike Johnson</td>
                                <td><span class="status status-in-progress">In Progress</span></td>
                                <td>
                                    <button class="btn btn-primary btn-sm">View</button>
                                </td>
                            </tr>
                            <tr>
                                <td>#ACR-1023</td>
                                <td>Sarah Wilson</td>
                                <td>AC Installation</td>
                                <td>11 May 2023</td>
                                <td>Robert Brown</td>
                                <td><span class="status status-completed">Completed</span></td>
                                <td>
                                    <button class="btn btn-primary btn-sm">View</button>
                                </td>
                            </tr>
                            <tr>
                                <td>#ACR-1022</td>
                                <td>David Miller</td>
                                <td>Maintenance</td>
                                <td>10 May 2023</td>
                                <td>James Davis</td>
                                <td><span class="status status-pending">Pending</span></td>
                                <td>
                                    <button class="btn btn-primary btn-sm">View</button>
                                </td>
                            </tr>
                            <tr>
                                <td>#ACR-1021</td>
                                <td>Lisa Anderson</td>
                                <td>AC Repair</td>
                                <td>09 May 2023</td>
                                <td>Mike Johnson</td>
                                <td><span class="status status-completed">Completed</span></td>
                                <td>
                                    <button class="btn btn-primary btn-sm">View</button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
            
            <!-- Service Requests Tab -->
            <div id="service-requests" class="tab-content">
                <div class="tabs">
                    <div class="tab active" onclick="showServiceTab('all-requests')">All Requests</div>
                    <div class="tab" onclick="showServiceTab('new-request')">New Request</div>
                </div>
                
                <div id="all-requests" class="service-tab-content active">
                    <div class="table-container">
                        <table>
                            <thead>
                                <tr>
                                    <th>ID</th>
                                    <th>Customer</th>
                                    <th>Service Type</th>
                                    <th>Date</th>
                                    <th>Technician</th>
                                    <th>Status</th>
                                    <th>Action</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>#ACR-1024</td>
                                    <td>John Smith</td>
                                    <td>AC Repair</td>
                                    <td>12 May 2023</td>
                                    <td>Mike Johnson</td>
                                    <td><span class="status status-in-progress">In Progress</span></td>
                                    <td>
                                        <button class="btn btn-primary btn-sm">View</button>
                                        <button class="btn btn-success btn-sm">Update</button>
                                    </td>
                                </tr>
                                <tr>
                                    <td>#ACR-1023</td>
                                    <td>Sarah Wilson</td>
                                    <td>AC Installation</td>
                                    <td>11 May 2023</td>
                                    <td>Robert Brown</td>
                                    <td><span class="status status-completed">Completed</span></td>
                                    <td>
                                        <button class="btn btn-primary btn-sm">View</button>
                                        <button class="btn btn-success btn-sm">Update</button>
                                    </td>
                                </tr>
                                <tr>
                                    <td>#ACR-1022</td>
                                    <td>David Miller</td>
                                    <td>Maintenance</td>
                                    <td>10 May 2023</td>
                                    <td>James Davis</td>
                                    <td><span class="status status-pending">Pending</span></td>
                                    <td>
                                        <button class="btn btn-primary btn-sm">View</button>
                                        <button class="btn btn-success btn-sm">Update</button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <div id="new-request" class="service-tab-content">
                    <div class="form-container">
                        <h3>Create New Service Request</h3>
                        <div class="form-row">
                            <div class="form-group">
                                <label for="customer">Customer</label>
                                <select id="customer">
                                    <option value="">Select Customer</option>
                                    <option value="1">John Smith</option>
                                    <option value="2">Sarah Wilson</option>
                                    <option value="3">David Miller</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label for="service-type">Service Type</label>
                                <select id="service-type">
                                    <option value="">Select Service Type</option>
                                    <option value="repair">AC Repair</option>
                                    <option value="installation">AC Installation</option>
                                    <option value="maintenance">Maintenance</option>
                                    <option value="cleaning">AC Cleaning</option>
                                </select>
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="date">Preferred Date</label>
                                <input type="date" id="date">
                            </div>
                            <div class="form-group">
                                <label for="technician">Assign Technician</label>
                                <select id="technician">
                                    <option value="">Select Technician</option>
                                    <option value="1">Mike Johnson</option>
                                    <option value="2">Robert Brown</option>
                                    <option value="3">James Davis</option>
                                </select>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="description">Problem Description</label>
                            <textarea id="description" rows="4"></textarea>
                        </div>
                        
                        <button class="btn btn-primary">Create Request</button>
                    </div>
                </div>
            </div>
            
            <!-- Technicians Tab -->
            <div id="technicians" class="tab-content">
                <div class="table-container">
                    <div style="display: flex; justify-content: space-between; align-items: center; padding: 15px;">
                        <h3>Technicians</h3>
                        <button class="btn btn-primary">Add Technician</button>
                    </div>
                    <table>
                        <thead>
                            <tr>
                                <th>ID</th>
                                <th>Name</th>
                                <th>Specialization</th>
                                <th>Contact</th>
                                <th>Assigned Jobs</th>
                                <th>Rating</th>
                                <th>Action</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr>
                                <td>T001</td>
                                <td>Mike Johnson</td>
                                <td>AC Repair, Installation</td>
                                <td>mike@example.com</td>
                                <td>12</td>
                                <td>4.8/5</td>
                                <td>
                                    <button class="btn btn-primary btn-sm">View</button>
                                    <button class="btn btn-success btn-sm">Edit</button>
                                </td>
                            </tr>
                            <tr>
                                <td>T002</td>
                                <td>Robert Brown</td>
                                <td>AC Installation, Maintenance</td>
                                <td>robert@example.com</td>
                                <td>8</td>
                                <td>4.7/5</td>
                                <td>
                                    <button class="btn btn-primary btn-sm">View</button>
                                    <button class="btn btn-success btn-sm">Edit</button>
                                </td>
                            </tr>
                            <tr>
                                <td>T003</td>
                                <td>James Davis</td>
                                <td>AC Repair, Cleaning</td>
                                <td>james@example.com</td>
                                <td>15</td>
                                <td>4.9/5</td>
                                <td>
                                    <button class="btn btn-primary btn-sm">View</button>
                                    <button class="btn btn-success btn-sm">Edit</button>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
            
            <!-- Other tabs would follow similar structure -->
            <div id="customers" class="tab-content">
                <h3>Customers Management</h3>
                <p>Customer list, details, and history would appear here.</p>
            </div>
            
            <div id="inventory" class="tab-content">
                <h3>Inventory Management</h3>
                <p>AC parts, tools, and supplies inventory would be managed here.</p>
            </div>
            
            <div id="reports" class="tab-content">
                <h3>Reports & Analytics</h3>
                <p>Service reports, revenue analytics, and performance metrics would appear here.</p>
            </div>
            
            <div id="settings" class="tab-content">
                <h3>System Settings</h3>
                <p>Admin settings, user management, and system configuration would appear here.</p>
            </div>
        </div>
    </div>

    <script>
        // Function to show main tabs
        function showTab(tabName) {
            // Hide all tab contents
            const tabContents = document.getElementsByClassName('tab-content');
            for (let i = 0; i < tabContents.length; i++) {
                tabContents[i].classList.remove('active');
            }
            
            // Show the selected tab content
            document.getElementById(tabName).classList.add('active');
            
            // Update page title
            const pageTitle = document.getElementById('page-title');
            const tabTitles = {
                'dashboard': 'Dashboard',
                'service-requests': 'Service Requests',
                'technicians': 'Technicians',
                'customers': 'Customers',
                'inventory': 'Inventory',
                'reports': 'Reports',
                'settings': 'Settings'
            };
            pageTitle.textContent = tabTitles[tabName];
            
            // Update active menu item
            const menuItems = document.querySelectorAll('.sidebar-menu li');
            for (let i = 0; i < menuItems.length; i++) {
                menuItems[i].classList.remove('active');
            }
            
            // Find and activate the clicked menu item
            for (let i = 0; i < menuItems.length; i++) {
                if (menuItems[i].getAttribute('onclick') === `showTab('${tabName}')`) {
                    menuItems[i].classList.add('active');
                    break;
                }
            }
        }
        
        // Function to show service request subtabs
        function showServiceTab(tabName) {
            // Hide all service tab contents
            const serviceTabContents = document.getElementsByClassName('service-tab-content');
            for (let i = 0; i < serviceTabContents.length; i++) {
                serviceTabContents[i].classList.remove('active');
            }
            
            // Show the selected service tab content
            document.getElementById(tabName).classList.add('active');
            
            // Update active service tab
            const serviceTabs = document.querySelectorAll('#service-requests .tab');
            for (let i = 0; i < serviceTabs.length; i++) {
                serviceTabs[i].classList.remove('active');
            }
            
            // Find and activate the clicked service tab
            for (let i = 0; i < serviceTabs.length; i++) {
                if (serviceTabs[i].getAttribute('onclick') === `showServiceTab('${tabName}')`) {
                    serviceTabs[i].classList.add('active');
                    break;
                }
            }
        }
    </script>
</body>
</html><!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CoolFix Pro - Appliance Repair Services</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #3498db;
            --secondary: #2c3e50;
            --accent: #e74c3c;
            --success: #2ecc71;
            --warning: #f39c12;
            --light: #f8f9fa;
            --dark: #343a40;
            --gray: #6c757d;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }
        
        /* Header Styles */
        header {
            background: linear-gradient(135deg, var(--secondary), var(--primary));
            color: white;
            padding: 15px 0;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .logo i {
            font-size: 28px;
            color: var(--accent);
        }
        
        .logo h1 {
            font-size: 24px;
            font-weight: 700;
        }
        
        .nav-menu {
            display: flex;
            list-style: none;
            gap: 25px;
        }
        
        .nav-menu a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: all 0.3s;
            padding: 5px 10px;
            border-radius: 4px;
        }
        
        .nav-menu a:hover, .nav-menu a.active {
            background: rgba(255,255,255,0.2);
        }
        
        .user-actions {
            display: flex;
            gap: 15px;
            align-items: center;
        }
        
        .btn {
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }
        
        .btn-primary {
            background: var(--accent);
            color: white;
        }
        
        .btn-primary:hover {
            background: #c0392b;
        }
        
        .btn-outline {
            background: transparent;
            border: 1px solid white;
            color: white;
        }
        
        .btn-outline:hover {
            background: white;
            color: var(--secondary);
        }
        
        /* Hero Section */
        .hero {
            background: linear-gradient(rgba(44, 62, 80, 0.8), rgba(52, 152, 219, 0.8)), url('https://images.unsplash.com/photo-1621905252507-b35492cc74b4?ixlib=rb-4.0.3&auto=format&fit=crop&w=1200&q=80');
            background-size: cover;
            background-position: center;
            color: white;
            padding: 80px 0;
            text-align: center;
        }
        
        .hero h2 {
            font-size: 42px;
            margin-bottom: 20px;
        }
        
        .hero p {
            font-size: 18px;
            max-width: 700px;
            margin: 0 auto 30px;
        }
        
        /* Services Section */
        .section {
            padding: 80px 0;
        }
        
        .section-title {
            text-align: center;
            margin-bottom: 50px;
        }
        
        .section-title h2 {
            font-size: 32px;
            color: var(--secondary);
            margin-bottom: 15px;
        }
        
        .section-title p {
            color: var(--gray);
            max-width: 600px;
            margin: 0 auto;
        }
        
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 30px;
        }
        
        .service-card {
            background: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            transition: transform 0.3s;
        }
        
        .service-card:hover {
            transform: translateY(-10px);
        }
        
        .service-icon {
            height: 120px;
            background: var(--primary);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 48px;
        }
        
        .service-content {
            padding: 25px;
        }
        
        .service-content h3 {
            font-size: 20px;
            margin-bottom: 15px;
            color: var(--secondary);
        }
        
        .service-content p {
            color: var(--gray);
            margin-bottom: 20px;
        }
        
        /* Booking Form */
        .booking-section {
            background: var(--light);
        }
        
        .booking-container {
            max-width: 800px;
            margin: 0 auto;
            background: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        
        .booking-header {
            background: var(--secondary);
            color: white;
            padding: 20px;
            text-align: center;
        }
        
        .booking-form {
            padding: 30px;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--dark);
        }
        
        input, select, textarea {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 16px;
            transition: border 0.3s;
        }
        
        input:focus, select:focus, textarea:focus {
            border-color: var(--primary);
            outline: none;
        }
        
        .form-row {
            display: flex;
            gap: 20px;
        }
        
        .form-row .form-group {
            flex: 1;
        }
        
        /* Request Status */
        .status-container {
            background: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        
        .status-header {
            padding: 20px;
            background: var(--light);
            border-bottom: 1px solid #eee;
        }
        
        .status-list {
            padding: 0;
        }
        
        .status-item {
            padding: 20px;
            border-bottom: 1px solid #eee;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .status-item:last-child {
            border-bottom: none;
        }
        
        .status-info h4 {
            margin-bottom: 5px;
            color: var(--secondary);
        }
        
        .status-info p {
            color: var(--gray);
            font-size: 14px;
        }
        
        .status-badge {
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 14px;
            font-weight: 600;
        }
        
        .status-pending {
            background: #fff3cd;
            color: #856404;
        }
        
        .status-confirmed {
            background: #d1ecf1;
            color: #0c5460;
        }
        
        .status-in-progress {
            background: #d4edda;
            color: #155724;
        }
        
        .status-completed {
            background: #d1ecf1;
            color: #0c5460;
        }
        
        /* Footer */
        footer {
            background: var(--secondary);
            color: white;
            padding: 60px 0 20px;
        }
        
        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            margin-bottom: 40px;
        }
        
        .footer-column h3 {
            font-size: 18px;
            margin-bottom: 20px;
            position: relative;
            padding-bottom: 10px;
        }
        
        .footer-column h3::after {
            content: '';
            position: absolute;
            left: 0;
            bottom: 0;
            width: 40px;
            height: 2px;
            background: var(--accent);
        }
        
        .footer-links {
            list-style: none;
        }
        
        .footer-links li {
            margin-bottom: 10px;
        }
        
        .footer-links a {
            color: #bbb;
            text-decoration: none;
            transition: color 0.3s;
        }
        
        .footer-links a:hover {
            color: white;
        }
        
        .contact-info {
            list-style: none;
        }
        
        .contact-info li {
            margin-bottom: 15px;
            display: flex;
            align-items: flex-start;
            gap: 10px;
        }
        
        .contact-info i {
            color: var(--accent);
            margin-top: 3px;
        }
        
        .copyright {
            text-align: center;
            padding-top: 20px;
            border-top: 1px solid rgba(255,255,255,0.1);
            color: #bbb;
            font-size: 14px;
        }
        
        /* Tabs */
        .tabs {
            display: flex;
            border-bottom: 1px solid #ddd;
            margin-bottom: 30px;
        }
        
        .tab {
            padding: 12px 25px;
            cursor: pointer;
            border-bottom: 3px solid transparent;
            font-weight: 600;
            color: var(--gray);
        }
        
        .tab.active {
            border-bottom: 3px solid var(--primary);
            color: var(--primary);
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
        
        /* Responsive */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 15px;
            }
            
            .nav-menu {
                gap: 15px;
            }
            
            .hero h2 {
                font-size: 32px;
            }
            
            .form-row {
                flex-direction: column;
                gap: 0;
            }
            
            .services-grid {
                grid-template-columns: 1fr;
            }
            
            .status-item {
                flex-direction: column;
                align-items: flex-start;
                gap: 10px;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container">
            <div class="header-content">
                <div class="logo">
                    <i class="fas fa-tools"></i>
                    <h1>CoolFix Pro</h1>
                </div>
                
                <ul class="nav-menu">
                    <li><a href="#" class="active">Home</a></li>
                    <li><a href="#services">Services</a></li>
                    <li><a href="#booking">Book Service</a></li>
                    <li><a href="#status">Request Status</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
                
                <div class="user-actions">
                    <button class="btn btn-outline"><i class="fas fa-user"></i> Login</button>
                    <button class="btn btn-primary"><i class="fas fa-phone-alt"></i> Emergency Call</button>
                </div>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero">
        <div class="container">
            <h2>Professional Appliance Repair Services</h2>
            <p>Fast, reliable, and affordable repair services for all your home appliances. Our certified technicians are ready to help 24/7.</p>
            <button class="btn btn-primary"><i class="fas fa-calendar-check"></i> Book Service Now</button>
        </div>
    </section>

    <!-- Services Section -->
    <section class="section" id="services">
        <div class="container">
            <div class="section-title">
                <h2>Our Repair Services</h2>
                <p>We specialize in repairing all types of cooling appliances with expert technicians and genuine parts.</p>
            </div>
            
            <div class="services-grid">
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-wind"></i>
                    </div>
                    <div class="service-content">
                        <h3>AC Repair & Service</h3>
                        <p>Professional AC repair, maintenance, and installation services for all brands and models.</p>
                        <button class="btn btn-primary">Book Now</button>
                    </div>
                </div>
                
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-snowflake"></i>
                    </div>
                    <div class="service-content">
                        <h3>Refrigerator Repair</h3>
                        <p>Expert refrigerator repair services including cooling issues, compressor problems, and more.</p>
                        <button class="btn btn-primary">Book Now</button>
                    </div>
                </div>
                
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-fan"></i>
                    </div>
                    <div class="service-content">
                        <h3>Chiller Repair</h3>
                        <p>Commercial and industrial chiller repair, maintenance, and installation services.</p>
                        <button class="btn btn-primary">Book Now</button>
                    </div>
                </div>
                
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-tint"></i>
                    </div>
                    <div class="service-content">
                        <h3>Water Cooler Repair</h3>
                        <p>Comprehensive water cooler repair services for both bottled and bottleless coolers.</p>
                        <button class="btn btn-primary">Book Now</button>
                    </div>
                </div>
                
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-temperature-low"></i>
                    </div>
                    <div class="service-content">
                        <h3>Deep Freezer Repair</h3>
                        <p>Expert deep freezer repair services including temperature issues and compressor problems.</p>
                        <button class="btn btn-primary">Book Now</button>
                    </div>
                </div>
                
                <div class="service-card">
                    <div class="service-icon">
                        <i class="fas fa-toolbox"></i>
                    </div>
                    <div class="service-content">
                        <h3>Maintenance Plans</h3>
                        <p>Regular maintenance plans to keep your appliances running efficiently and extend their lifespan.</p>
                        <button class="btn btn-primary">View Plans</button>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Booking Section -->
    <section class="section booking-section" id="booking">
        <div class="container">
            <div class="section-title">
                <h2>Book a Service</h2>
                <p>Fill out the form below to schedule a repair service at your convenience.</p>
            </div>
            
            <div class="booking-container">
                <div class="booking-header">
                    <h3><i class="fas fa-calendar-alt"></i> Schedule Your Repair</h3>
                </div>
                
                <div class="booking-form">
                    <form id="serviceBookingForm">
                        <div class="form-row">
                            <div class="form-group">
                                <label for="name">Full Name</label>
                                <input type="text" id="name" placeholder="Enter your full name" required>
                            </div>
                            <div class="form-group">
                                <label for="phone">Phone Number</label>
                                <input type="tel" id="phone" placeholder="Enter your phone number" required>
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="email">Email Address</label>
                                <input type="email" id="email" placeholder="Enter your email address">
                            </div>
                            <div class="form-group">
                                <label for="address">Service Address</label>
                                <input type="text" id="address" placeholder="Enter your complete address" required>
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="service">Service Type</label>
                                <select id="service" required>
                                    <option value="">Select a service</option>
                                    <option value="ac-repair">AC Repair & Service</option>
                                    <option value="refrigerator">Refrigerator Repair</option>
                                    <option value="chiller">Chiller Repair</option>
                                    <option value="water-cooler">Water Cooler Repair</option>
                                    <option value="deep-freezer">Deep Freezer Repair</option>
                                    <option value="maintenance">Maintenance Service</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label for="date">Preferred Date</label>
                                <input type="date" id="date" required>
                            </div>
                        </div>
                        
                        <div class="form-group">
                            <label for="problem">Problem Description</label>
                            <textarea id="problem" rows="4" placeholder="Please describe the issue with your appliance" required></textarea>
                        </div>
                        
                        <button type="submit" class="btn btn-primary" style="width: 100%;">
                            <i class="fas fa-paper-plane"></i> Submit Service Request
                        </button>
                    </form>
                </div>
            </div>
        </div>
    </section>

    <!-- Request Status Section -->
    <section class="section" id="status">
        <div class="container">
            <div class="section-title">
                <h2>Service Request Status</h2>
                <p>Track the status of your repair requests in real-time.</p>
            </div>
            
            <div class="tabs">
                <div class="tab active" onclick="showStatusTab('active')">Active Requests</div>
                <div class="tab" onclick="showStatusTab('completed')">Completed Services</div>
            </div>
            
            <div id="active" class="tab-content active">
                <div class="status-container">
                    <div class="status-header">
                        <h3><i class="fas fa-tasks"></i> Your Active Service Requests</h3>
                    </div>
                    
                    <div class="status-list">
                        <div class="status-item">
                            <div class="status-info">
                                <h4>AC Repair - Split Unit</h4>
                                <p>Request ID: #ACR-230512 | Submitted: May 12, 2023</p>
                                <p>Technician: Mike Johnson | Scheduled: May 15, 2023</p>
                            </div>
                            <div class="status-badge status-in-progress">In Progress</div>
                        </div>
                        
                        <div class="status-item">
                            <div class="status-info">
                                <h4>Refrigerator Not Cooling</h4>
                                <p>Request ID: #REF-230510 | Submitted: May 10, 2023</p>
                                <p>Technician: Robert Brown | Scheduled: May 13, 2023</p>
                            </div>
                            <div class="status-badge status-confirmed">Confirmed</div>
                        </div>
                    </div>
                </div>
            </div>
            
            <div id="completed" class="tab-content">
                <div class="status-container">
                    <div class="status-header">
                        <h3><i class="fas fa-clipboard-check"></i> Completed Services</h3>
                    </div>
                    
                    <div class="status-list">
                        <div class="status-item">
                            <div class="status-info">
                                <h4>Water Cooler Repair</h4>
                                <p>Request ID: #WCR-230505 | Completed: May 8, 2023</p>
                                <p>Technician: James Davis | Service Charge: $85</p>
                            </div>
                            <div class="status-badge status-completed">Completed</div>
                        </div>
                        
                        <div class="status-item">
                            <div class="status-info">
                                <h4>Deep Freezer Maintenance</h4>
                                <p>Request ID: #DFM-230428 | Completed: May 2, 2023</p>
                                <p>Technician: Sarah Wilson | Service Charge: $65</p>
                            </div>
                            <div class="status-badge status-completed">Completed</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer id="contact">
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>CoolFix Pro</h3>
                    <p>Professional appliance repair services with certified technicians and genuine parts. We're committed to providing fast, reliable, and affordable solutions.</p>
                    <div class="user-actions" style="margin-top: 20px;">
                        <button class="btn btn-primary"><i class="fas fa-phone-alt"></i> Call Now</button>
                    </div>
                </div>
                
                <div class="footer-column">
                    <h3>Quick Links</h3>
                    <ul class="footer-links">
                        <li><a href="#">Home</a></li>
                        <li><a href="#services">Services</a></li>
                        <li><a href="#booking">Book Service</a></li>
                        <li><a href="#status">Request Status</a></li>
                        <li><a href="#">About Us</a></li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Our Services</h3>
                    <ul class="footer-links">
                        <li><a href="#">AC Repair & Service</a></li>
                        <li><a href="#">Refrigerator Repair</a></li>
                        <li><a href="#">Chiller Repair</a></li>
                        <li><a href="#">Water Cooler Repair</a></li>
                        <li><a href="#">Deep Freezer Repair</a></li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Contact Us</h3>
                    <ul class="contact-info">
                        <li>
                            <i class="fas fa-map-marker-alt"></i>
                            <span>123 Repair Street, Service City, SC 12345</span>
                        </li>
                        <li>
                            <i class="fas fa-phone"></i>
                            <span>+1 (555) 123-4567</span>
                        </li>
                        <li>
                            <i class="fas fa-envelope"></i>
                            <span>support@coolfixpro.com</span>
                        </li>
                        <li>
                            <i class="fas fa-clock"></i>
                            <span>Mon-Sun: 8:00 AM - 10:00 PM</span>
                        </li>
                    </ul>
                </div>
            </div>
            
            <div class="copyright">
                <p>&copy; 2023 CoolFix Pro. All rights reserved. | Professional Appliance Repair Services</p>
            </div>
        </div>
    </footer>

    <script>
        // Form submission
        document.getElementById('serviceBookingForm').addEventListener('submit', function(e) {
            e.preventDefault();
            alert('Thank you! Your service request has been submitted. We will contact you shortly.');
            this.reset();
        });
        
        // Tab functionality for status section
        function showStatusTab(tabName) {
            // Hide all tab contents
            const tabContents = document.querySelectorAll('#status .tab-content');
            tabContents.forEach(tab => {
                tab.classList.remove('active');
            });
            
            // Show the selected tab content
            document.getElementById(tabName).classList.add('active');
            
            // Update active tab
            const tabs = document.querySelectorAll('#status .tab');
            tabs.forEach(tab => {
                tab.classList.remove('active');
            });
            
            // Find and activate the clicked tab
            event.target.classList.add('active');
        }
        
        // Smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                if(targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if(targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 80,
                        behavior: 'smooth'
                    });
                }
            });
        });
        
        // Set minimum date for booking to today
        const today = new Date().toISOString().split('T')[0];
        document.getElementById('date').setAttribute('min', today);
    </script>
</body>
</html>
