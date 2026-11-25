<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Nexus Student Portal</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet" />
  <style>
    :root {
      --bg: #f4f6fb;
      --surface: #ffffff;
      --surface-subtle: #f8fafc;
      --text: #0f172a;
      --muted: #64748b;
      --border: #e2e8f0;
      --primary: #4f46e5;
      --primary-hover: #4338ca;
      --primary-soft: #eef2ff;
      --success: #059669;
      --success-soft: #ecfdf5;
      --warning: #d97706;
      --warning-soft: #fffbeb;
      --danger: #dc2626;
      --danger-soft: #fef2f2;
      --radius: 14px;
      --shadow: 0 4px 20px -4px rgba(15, 23, 42, 0.06);
    }

    [data-theme="dark"] {
      --bg: #0b1020;
      --surface: #12192f;
      --surface-subtle: #18223f;
      --text: #f1f5f9;
      --muted: #94a3b8;
      --border: #243052;
      --primary: #6366f1;
      --primary-hover: #818cf8;
      --primary-soft: rgba(99, 102, 241, 0.16);
      --success: #34d399;
      --success-soft: rgba(52, 211, 153, 0.14);
      --warning: #fbbf24;
      --warning-soft: rgba(251, 191, 36, 0.14);
      --danger: #f87171;
      --danger-soft: rgba(248, 113, 113, 0.14);
      --shadow: 0 8px 24px -6px rgba(0, 0, 0, 0.45);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
      background: var(--bg);
      color: var(--text);
      line-height: 1.5;
      transition: background 0.2s ease, color 0.2s ease;
    }

    .app-shell {
      display: grid;
      grid-template-columns: 250px 1fr;
      min-height: 100vh;
    }

    /* Sidebar */
    .sidebar {
      background: var(--surface);
      border-right: 1px solid var(--border);
      padding: 24px 16px;
      display: flex;
      flex-direction: column;
      gap: 24px;
      position: sticky;
      top: 0;
      height: 100vh;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 0 8px;
    }

    .brand-logo {
      width: 38px;
      height: 38px;
      border-radius: 10px;
      background: linear-gradient(135deg, var(--primary), #06b6d4);
      color: #fff;
      font-weight: 700;
      display: grid;
      place-items: center;
      font-size: 1.05rem;
    }

    .brand-title {
      font-weight: 700;
      font-size: 1rem;
      letter-spacing: -0.01em;
    }

    .brand-sub {
      font-size: 0.75rem;
      color: var(--muted);
    }

    .nav-list {
      display: flex;
      flex-direction: column;
      gap: 6px;
    }

    .nav-btn {
      width: 100%;
      border: none;
      background: transparent;
      color: var(--muted);
      font-family: inherit;
      font-size: 0.92rem;
      font-weight: 500;
      padding: 10px 14px;
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      cursor: pointer;
      transition: all 0.15s ease;
      text-align: left;
    }

    .nav-btn:hover {
      background: var(--surface-subtle);
      color: var(--text);
    }

    .nav-btn.active {
      background: var(--primary-soft);
      color: var(--primary);
      font-weight: 600;
    }

    .nav-badge {
      font-size: 0.72rem;
      font-weight: 600;
      padding: 2px 8px;
      border-radius: 999px;
      background: var(--primary);
      color: #fff;
    }

    .sidebar-footer {
      margin-top: auto;
      padding: 14px;
      border-radius: 12px;
      background: var(--surface-subtle);
      border: 1px solid var(--border);
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .avatar {
      width: 40px;
      height: 40px;
      border-radius: 50%;
      background: var(--primary-soft);
      color: var(--primary);
      font-weight: 700;
      display: grid;
      place-items: center;
      flex-shrink: 0;
    }

    /* Main Content */
    .main {
      padding: 28px 36px;
      max-width: 1240px;
      width: 100%;
      margin: 0 auto;
    }

    .topbar {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
      margin-bottom: 28px;
    }

    .page-title {
      font-size: 1.65rem;
      font-weight: 700;
      letter-spacing: -0.02em;
    }

    .page-subtitle {
      color: var(--muted);
      font-size: 0.9rem;
      margin-top: 2px;
    }

    .topbar-actions {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .btn {
      border: 1px solid var(--border);
      background: var(--surface);
      color: var(--text);
      font-family: inherit;
      font-size: 0.875rem;
      font-weight: 500;
      padding: 9px 14px;
      border-radius: 10px;
      cursor: pointer;
      transition: all 0.15s ease;
    }

    .btn:hover {
      background: var(--surface-subtle);
    }

    .btn-primary {
      background: var(--primary);
      border-color: var(--primary);
      color: #fff;
    }

    .btn-primary:hover {
      background: var(--primary-hover);
    }

    /* Cards & Grids */
    .grid-4 {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(210px, 1fr));
      gap: 18px;
      margin-bottom: 24px;
    }

    .grid-2 {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
      gap: 20px;
    }

    .card {
      background: var(--surface);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 20px;
      box-shadow: var(--shadow);
    }

    .stat-label {
      font-size: 0.8rem;
      font-weight: 600;
      color: var(--muted);
      text-transform: uppercase;
      letter-spacing: 0.04em;
    }

    .stat-value {
      font-size: 1.85rem;
      font-weight: 700;
      margin: 6px 0 4px;
      letter-spacing: -0.02em;
    }

    .stat-meta {
      font-size: 0.82rem;
      color: var(--muted);
    }

    .card-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      margin-bottom: 16px;
    }

    .card-title {
      font-size: 1.05rem;
      font-weight: 600;
    }

    /* Pills & Badges */
    .pill {
      display: inline-flex;
      align-items: center;
      padding: 3px 10px;
      border-radius: 999px;
      font-size: 0.76rem;
      font-weight: 600;
    }

    .pill-indigo { background: var(--primary-soft); color: var(--primary); }
    .pill-green { background: var(--success-soft); color: var(--success); }
    .pill-amber { background: var(--warning-soft); color: var(--warning); }
    .pill-red { background: var(--danger-soft); color: var(--danger); }

    /* Filter Bar */
    .filter-bar {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-bottom: 18px;
    }

    .chip {
      border: 1px solid var(--border);
      background: var(--surface);
      color: var(--muted);
      font-family: inherit;
      font-size: 0.84rem;
      font-weight: 500;
      padding: 6px 14px;
      border-radius: 999px;
      cursor: pointer;
    }

    .chip.active {
      background: var(--primary);
      border-color: var(--primary);
      color: #fff;
    }

    .search-input, .field-input, .field-textarea, .field-select {
      width: 100%;
      border: 1px solid var(--border);
      background: var(--surface-subtle);
      color: var(--text);
      font-family: inherit;
      font-size: 0.9rem;
      padding: 10px 12px;
      border-radius: 10px;
    }

    .search-input {
      max-width: 280px;
    }

    /* Tables */
    .table-wrap {
      overflow-x: auto;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      font-size: 0.9rem;
    }

    th, td {
      text-align: left;
      padding: 12px 14px;
      border-bottom: 1px solid var(--border);
    }

    th {
      font-size: 0.76rem;
      text-transform: uppercase;
      letter-spacing: 0.04em;
      color: var(--muted);
      font-weight: 600;
    }

    tr:last-child td {
      border-bottom: none;
    }

    /* Announcements */
    .announcement-item {
      padding: 16px;
      border: 1px solid var(--border);
      border-radius: 12px;
      background: var(--surface-subtle);
      margin-bottom: 12px;
      transition: border-color 0.15s ease;
    }

    .announcement-item.unread {
      border-left: 4px solid var(--primary);
    }

    .announcement-top {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 8px;
      margin-bottom: 6px;
    }

    .announcement-title {
      font-weight: 600;
      font-size: 0.98rem;
    }

    .announcement-date {
      font-size: 0.78rem;
      color: var(--muted);
    }

    /* Form */
    .form-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 14px;
    }

    .form-group {
      display: flex;
      flex-direction: column;
      gap: 6px;
      margin-bottom: 14px;
    }

    label {
      font-size: 0.82rem;
      font-weight: 600;
      color: var(--muted);
    }

    .toast {
      position: fixed;
      bottom: 22px;
      right: 22px;
      background: var(--text);
      color: var(--surface);
      padding: 11px 16px;
      border-radius: 10px;
      font-size: 0.86rem;
      font-weight: 500;
      opacity: 0;
      transform: translateY(10px);
      pointer-events: none;
      transition: all 0.2s ease;
      z-index: 50;
    }

    .toast.show {
      opacity: 1;
      transform: translateY(0);
    }

    .view { display: none; }
    .view.active { display: block; }

    @media (max-width: 860px) {
      .app-shell {
        grid-template-columns: 1fr;
      }
      .sidebar {
        position: static;
        height: auto;
        border-right: none;
        border-bottom: 1px solid var(--border);
      }
      .nav-list {
        flex-direction: row;
        overflow-x: auto;
        padding-bottom: 4px;
      }
      .nav-btn {
        width: auto;
        white-space: nowrap;
      }
      .sidebar-footer {
        display: none;
      }
      .main {
        padding: 20px 16px;
      }
    }
  </style>
</head>
<body>
  <div class="app-shell">
    <aside class="sidebar">
      <div class="brand">
        <div class="brand-logo">N</div>
        <div>
          <div class="brand-title">Nexus Portal</div>
          <div class="brand-sub">Fall Term 2026</div>
        </div>
      </div>

      <nav class="nav-list" aria-label="Primary Navigation">
        <button class="nav-btn active" data-view="dashboard">Dashboard</button>
        <button class="nav-btn" data-view="schedule">Class Schedule</button>
        <button class="nav-btn" data-view="grades">Grades</button>
        <button class="nav-btn" data-view="announcements">
          Announcements
          <span class="nav-badge" id="unreadBadge">0</span>
        </button>
        <button class="nav-btn" data-view="profile">Student Profile</button>
      </nav>

      <div class="sidebar-footer">
        <div class="avatar" id="sidebarAvatar">AT</div>
        <div style="min-width: 0;">
          <div id="sidebarName" style="font-weight: 600; font-size: 0.88rem; white-space: nowrap; overflow: hidden; text-overflow: ellipsis;">Alex Tan</div>
          <div id="sidebarId" style="font-size: 0.75rem; color: var(--muted);">ID: 2024-08192</div>
        </div>
      </div>
    </aside>

    <main class="main">
      <header class="topbar">
        <div>
          <h1 class="page-title" id="pageTitle">Dashboard</h1>
          <p class="page-subtitle" id="pageSubtitle">Welcome back — here is your academic snapshot.</p>
        </div>
        <div class="topbar-actions">
          <button class="btn" id="themeToggle" type="button">Toggle Theme</button>
        </div>
      </header>

      <!-- DASHBOARD -->
      <section class="view active" id="view-dashboard">
        <div class="grid-4" id="dashStats"></div>

        <div class="grid-2">
          <div class="card">
            <div class="card-header">
              <h2 class="card-title">Today's Classes</h2>
              <button class="btn" data-jump="schedule">Full Schedule</button>
            </div>
            <div id="dashTodayClasses"></div>
          </div>

          <div class="card">
            <div class="card-header">
              <h2 class="card-title">Latest Announcements</h2>
              <button class="btn" data-jump="announcements">View All</button>
            </div>
            <div id="dashAnnouncements"></div>
          </div>
        </div>
      </section>

      <!-- SCHEDULE -->
      <section class="view" id="view-schedule">
        <div class="card">
          <div class="card-header">
            <h2 class="card-title">Weekly Timetable</h2>
          </div>
          <div class="filter-bar" id="scheduleFilters">
            <button class="chip active" data-day="ALL">All Days</button>
            <button class="chip" data-day="MWF">Mon / Wed / Fri</button>
            <button class="chip" data-day="TTH">Tue / Thu</button>
          </div>
          <div class="table-wrap">
            <table>
              <thead>
                <tr>
                  <th>Course</th>
                  <th>Schedule</th>
                  <th>Time</th>
                  <th>Location</th>
                  <th>Instructor</th>
                </tr>
              </thead>
              <tbody id="scheduleBody"></tbody>
            </table>
          </div>
        </div>
      </section>

      <!-- GRADES -->
      <section class="view" id="view-grades">
        <div class="grid-4" id="gradeSummary"></div>
        <div class="card">
          <div class="card-header">
            <div>
              <h2 class="card-title">Course Grades &amp; What-If Simulator</h2>
              <p class="page-subtitle">Adjust a course's simulated score (%) to preview your projected GPA.</p>
            </div>
            <button class="btn" id="resetGradesBtn" type="button">Reset Scores</button>
          </div>
          <div class="table-wrap">
            <table>
              <thead>
                <tr>
                  <th>Course</th>
                  <th>Credits</th>
                  <th>Current Score</th>
                  <th>Simulated Score (%)</th>
                  <th>Grade</th>
                  <th>Grade Points</th>
                </tr>
              </thead>
              <tbody id="gradesBody"></tbody>
            </table>
          </div>
        </div>
      </section>

      <!-- ANNOUNCEMENTS -->
      <section class="view" id="view-announcements">
        <div class="card">
          <div class="card-header">
            <h2 class="card-title">Campus &amp; Course Notices</h2>
            <input class="search-input" type="search" id="announcementSearch" placeholder="Search announcements..." />
          </div>
          <div class="filter-bar" id="announcementFilters">
            <button class="chip active" data-cat="ALL">All</button>
            <button class="chip" data-cat="Academic">Academic</button>
            <button class="chip" data-cat="Deadlines">Deadlines</button>
            <button class="chip" data-cat="Campus">Campus</button>
          </div>
          <div id="announcementsList"></div>
        </div>
      </section>

      <!-- PROFILE -->
      <section class="view" id="view-profile">
        <div class="grid-2">
          <div class="card">
            <h2 class="card-title" style="margin-bottom: 16px;">Student Information</h2>
            <form id="profileForm">
              <div class="form-grid">
                <div class="form-group">
                  <label for="profName">Full Name</label>
                  <input class="field-input" id="profName" type="text" required />
                </div>
                <div class="form-group">
                  <label for="profId">Student ID</label>
                  <input class="field-input" id="profId" type="text" required />
                </div>
              </div>
              <div class="form-grid">
                <div class="form-group">
                  <label for="profProgram">Degree Program</label>
                  <input class="field-input" id="profProgram" type="text" required />
                </div>
                <div class="form-group">
                  <label for="profYear">Year Level</label>
                  <select class="field-select" id="profYear">
                    <option>1st Year</option>
                    <option>2nd Year</option>
                    <option>3rd Year</option>
                    <option>4th Year</option>
                  </select>
                </div>
              </div>
              <div class="form-group">
                <label for="profEmail">University Email</label>
                <input class="field-input" id="profEmail" type="email" required />
              </div>
              <div class="form-group">
                <label for="profBio">Academic Bio &amp; Interests</label>
                <textarea class="field-textarea" id="profBio" rows="3"></textarea>
              </div>
              <div style="display: flex; gap: 10px; flex-wrap: wrap;">
                <button class="btn btn-primary" type="submit">Save Profile</button>
                <button class="btn" id="resetDemoBtn" type="button">Reset All Demo Data</button>
              </div>
            </form>
          </div>

          <div class="card">
            <h2 class="card-title" style="margin-bottom: 16px;">Profile Summary</h2>
            <div style="display: flex; align-items: center; gap: 14px; margin-bottom: 16px;">
              <div class="avatar" id="profAvatar" style="width: 56px; height: 56px; font-size: 1.2rem;">AT</div>
              <div>
                <div id="profPreviewName" style="font-size: 1.15rem; font-weight: 700;"></div>
                <div id="profPreviewProgram" style="color: var(--muted); font-size: 0.9rem;"></div>
              </div>
            </div>
            <p id="profPreviewBio" style="font-size: 0.92rem; color: var(--muted); margin-bottom: 16px;"></p>
            <div style="font-size: 0.85rem; display: grid; gap: 8px;">
              <div><strong>Student ID:</strong> <span id="profPreviewId"></span></div>
              <div><strong>Email:</strong> <span id="profPreviewEmail"></span></div>
              <div><strong>Storage Mode:</strong> Browser <code>localStorage</code> (Static GitHub Pages)</div>
            </div>
          </div>
        </div>
      </section>
    </main>
  </div>

  <div class="toast" id="toast" role="status" aria-live="polite"></div>

  <script>
    const STORAGE_KEY = "nexus_student_portal_v1";

    const DEFAULT_STATE = {
      theme: "light",
      profile: {
        name: "Alex Tan",
        studentId: "2024-08192",
        program: "B.S. Computer Science",
        year: "3rd Year",
        email: "alex.tan@university.edu",
        bio: "Interested in distributed systems, human-computer interaction, and open-source web tooling."
      },
      courses: [
        { code: "CS 301", name: "Algorithms & Data Structures", credits: 4, score: 94, simScore: 94, days: "MWF", time: "09:00 - 10:00 AM", room: "Eng Hall 204", instructor: "Dr. M. Santos" },
        { code: "CS 315", name: "Database Systems", credits: 3, score: 89, simScore: 89, days: "MWF", time: "11:00 - 12:00 PM", room: "Tech Lab 102", instructor: "Prof. R. Lim" },
        { code: "MATH 240", name: "Linear Algebra & Probability", credits: 3, score: 86, simScore: 86, days: "TTH", time: "09:30 - 11:00 AM", room: "Science 310", instructor: "Dr. K. Reyes" },
        { code: "CS 340", name: "Human-Computer Interaction", credits: 3, score: 96, simScore: 96, days: "TTH", time: "01:30 - 03:00 PM", room: "Design Studio B", instructor: "Prof. J. Cruz" },
        { code: "HUM 210", name: "Ethics in Emerging Tech", credits: 2, score: 91, simScore: 91, days: "MWF", time: "02:00 - 03:00 PM", room: "Liberal Arts 108", instructor: "Dr. A. Navarro" }
      ],
      announcements: [
        { id: "a1", title: "Final Project Proposal Guidelines Posted", category: "Academic", date: "Nov 24, 2026", unread: true, body: "Teams of 2–3 should submit their one-page problem statement and architecture outline by Friday at 5:00 PM." },
        { id: "a2", title: "Course Add/Drop & Withdrawal Deadline", category: "Deadlines", date: "Nov 22, 2026", unread: true, body: "Please confirm your enrolled credit load before November 30 to avoid late administrative adjustments." },
        { id: "a3", title: "24-Hour Library Study Zone During Finals Prep", category: "Campus", date: "Nov 19, 2026", unread: false, body: "The main library's 2nd floor will stay open overnight starting next Monday with student ID tap access." },
        { id: "a4", title: "Database Lab #4 Rubrics & Sample Dataset", category: "Academic", date: "Nov 15, 2026", unread: false, body: "Indexing benchmarks and query plan screenshots are now included in the lab grading checklist." }
      ]
    };

    let state = loadState();
    let activeView = "dashboard";
    let scheduleFilter = "ALL";
    let announcementFilter = "ALL";
    let announcementQuery = "";

    function loadState() {
      try {
        const raw = localStorage.getItem(STORAGE_KEY);
        if (!raw) return structuredClone(DEFAULT_STATE);
        return { ...structuredClone(DEFAULT_STATE), ...JSON.parse(raw) };
      } catch {
        return structuredClone(DEFAULT_STATE);
      }
    }

    function saveState() {
      localStorage.setItem(STORAGE_KEY, JSON.stringify(state));
    }

    function showToast(msg) {
      const el = document.getElementById("toast");
      el.textContent = msg;
      el.classList.add("show");
      clearTimeout(showToast._t);
      showToast._t = setTimeout(() => el.classList.remove("show"), 2200);
    }

    function initials(name) {
      return name.trim().split(/\s+/).slice(0, 2).map(p => p[0]?.toUpperCase() || "").join("") || "ST";
    }

    function scoreToGpa(score) {
      if (score >= 93) return { letter: "A", points: 4.0, pill: "pill-green" };
      if (score >= 90) return { letter: "A-", points: 3.7, pill: "pill-green" };
      if (score >= 87) return { letter: "B+", points: 3.3, pill: "pill-indigo" };
      if (score >= 83) return { letter: "B", points: 3.0, pill: "pill-indigo" };
      if (score >= 80) return { letter: "B-", points: 2.7, pill: "pill-amber" };
      if (score >= 75) return { letter: "C", points: 2.0, pill: "pill-amber" };
      return { letter: "D/F", points: 1.0, pill: "pill-red" };
    }

    function calcGpa(useSimulated = false) {
      const totalCredits = state.courses.reduce((acc, c) => acc + c.credits, 0);
      const weighted = state.courses.reduce((acc, c) => {
        const s = useSimulated ? c.simScore : c.score;
        return acc + scoreToGpa(s).points * c.credits;
      }, 0);
      return {
        gpa: totalCredits ? (weighted / totalCredits).toFixed(2) : "0.00",
        totalCredits
      };
    }

    function applyTheme() {
      document.documentElement.setAttribute("data-theme", state.theme);
    }

    function setView(viewName) {
      activeView = viewName;
      document.querySelectorAll(".nav-btn").forEach(btn => {
        btn.classList.toggle("active", btn.dataset.view === viewName);
      });
      document.querySelectorAll(".view").forEach(v => {
        v.classList.toggle("active", v.id === `view-${viewName}`);
      });

      const meta = {
        dashboard: ["Dashboard", `Welcome back, ${state.profile.name.split(" ")[0]} — here is your academic snapshot.`],
        schedule: ["Class Schedule", "Weekly courses, rooms, and instructors."],
        grades: ["Grades & GPA", "Track current performance and simulate final exam scores."],
        announcements: ["Announcements", "Stay up to date with academic notices and deadlines."],
        profile: ["Student Profile", "Manage your personal details and local browser preferences."]
      }[viewName];

      document.getElementById("pageTitle").textContent = meta[0];
      document.getElementById("pageSubtitle").textContent = meta[1];
      render();
    }

    function renderAll() {
      applyTheme();
      const ini = initials(state.profile.name);
      document.getElementById("sidebarAvatar").textContent = ini;
      document.getElementById("sidebarName").textContent = state.profile.name;
      document.getElementById("sidebarId").textContent = `ID: ${state.profile.studentId}`;

      const unreadCount = state.announcements.filter(a => a.unread).length;
      const badge = document.getElementById("unreadBadge");
      badge.textContent = unreadCount;
      badge.style.display = unreadCount ? "inline-block" : "none";

      renderDashboard();
      renderSchedule();
      renderGrades();
      renderAnnouncements();
      renderProfile();
    }

    function render() {
      renderAll();
    }

    function renderDashboard() {
      const { gpa, totalCredits } = calcGpa(false);
      const unreadCount = state.announcements.filter(a => a.unread).length;

      document.getElementById("dashStats").innerHTML = `
        <div class="card">
          <div class="stat-label">Cumulative GPA</div>
          <div class="stat-value">${gpa}</div>
          <div class="stat-meta">4.00 scale • ${state.profile.year}</div>
        </div>
        <div class="card">
          <div class="stat-label">Enrolled Credits</div>
          <div class="stat-value">${totalCredits}</div>
          <div class="stat-meta">${state.courses.length} active courses</div>
        </div>
        <div class="card">
          <div class="stat-label">Unread Notices</div>
          <div class="stat-value">${unreadCount}</div>
          <div class="stat-meta">Announcements &amp; deadlines</div>
        </div>
        <div class="card">
          <div class="stat-label">Program</div>
          <div class="stat-value" style="font-size: 1.2rem; padding-top: 6px;">${state.profile.program}</div>
          <div class="stat-meta">${state.profile.studentId}</div>
        </div>
      `;

      document.getElementById("dashTodayClasses").innerHTML = state.courses.slice(0, 3).map(c => `
        <div style="display:flex; justify-content:space-between; align-items:center; padding:10px 0; border-bottom:1px solid var(--border);">
          <div>
            <div style="font-weight:600;">${c.code} • ${c.name}</div>
            <div style="font-size:0.82rem; color:var(--muted);">${c.days} (${c.time}) • ${c.room}</div>
          </div>
          <span class="pill pill-indigo">${c.instructor}</span>
        </div>
      `).join("");

      document.getElementById("dashAnnouncements").innerHTML = state.announcements.slice(0, 3).map(a => `
        <div style="padding:10px 0; border-bottom:1px solid var(--border);">
          <div style="display:flex; justify-content:space-between; gap:8px;">
            <strong style="font-size:0.92rem;">${a.title}</strong>
            <span class="pill pill-amber">${a.category}</span>
          </div>
          <div style="font-size:0.8rem; color:var(--muted); margin-top:4px;">${a.date}</div>
        </div>
      `).join("");
    }

    function renderSchedule() {
      const rows = state.courses.filter(c => scheduleFilter === "ALL" || c.days === scheduleFilter);
      document.getElementById("scheduleBody").innerHTML = rows.map(c => `
        <tr>
          <td><strong>${c.code}</strong> — ${c.name}</td>
          <td><span class="pill pill-indigo">${c.days}</span></td>
          <td>${c.time}</td>
          <td>${c.room}</td>
          <td>${c.instructor}</td>
        </tr>
      `).join("");
    }

    function renderGrades() {
      const current = calcGpa(false);
      const sim = calcGpa(true);

      document.getElementById("gradeSummary").innerHTML = `
        <div class="card">
          <div class="stat-label">Current GPA</div>
          <div class="stat-value">${current.gpa}</div>
          <div class="stat-meta">Based on recorded scores</div>
        </div>
        <div class="card">
          <div class="stat-label">Simulated GPA</div>
          <div class="stat-value">${sim.gpa}</div>
          <div class="stat-meta">Live what-if projection</div>
        </div>
        <div class="card">
          <div class="stat-label">Total Credits</div>
          <div class="stat-value">${current.totalCredits}</div>
          <div class="stat-meta">Credit-weighted</div>
        </div>
      `;

      document.getElementById("gradesBody").innerHTML = state.courses.map((c, idx) => {
        const g = scoreToGpa(c.simScore);
        return `
          <tr>
            <td><strong>${c.code}</strong> — ${c.name}</td>
            <td>${c.credits}</td>
            <td>${c.score}%</td>
            <td>
              <input type="number" min="0" max="100" value="${c.simScore}" data-sim-idx="${idx}"
                class="field-input" style="max-width: 90px; padding: 6px 10px;" />
            </td>
            <td><span class="pill ${g.pill}">${g.letter}</span></td>
            <td>${g.points.toFixed(1)}</td>
          </tr>
        `;
      }).join("");

      document.querySelectorAll("[data-sim-idx]").forEach(input => {
        input.addEventListener("input", e => {
          const i = Number(e.target.dataset.simIdx);
          const val = Math.max(0, Math.min(100, Number(e.target.value) || 0));
          state.courses[i].simScore = val;
          saveState();
          renderGrades();
        });
      });
    }

    function renderAnnouncements() {
      const filtered = state.announcements.filter(a => {
        const matchesCat = announcementFilter === "ALL" || a.category === announcementFilter;
        const q = announcementQuery.trim().toLowerCase();
        const matchesQuery = !q || a.title.toLowerCase().includes(q) || a.body.toLowerCase().includes(q);
        return matchesCat && matchesQuery;
      });

      const container = document.getElementById("announcementsList");
      if (!filtered.length) {
        container.innerHTML = `<p style="color:var(--muted); padding:12px 0;">No announcements match your filter.</p>`;
        return;
      }

      container.innerHTML = filtered.map(a => `
        <div class="announcement-item ${a.unread ? "unread" : ""}">
          <div class="announcement-top">
            <div>
              <span class="announcement-title">${a.title}</span>
              <span class="pill pill-indigo" style="margin-left:8px;">${a.category}</span>
            </div>
            <div style="display:flex; align-items:center; gap:10px;">
              <span class="announcement-date">${a.date}</span>
              <button class="btn" style="padding:5px 10px; font-size:0.78rem;" data-toggle-read="${a.id}">
                ${a.unread ? "Mark Read" : "Mark Unread"}
              </button>
            </div>
          </div>
          <p style="font-size:0.9rem; color:var(--muted);">${a.body}</p>
        </div>
      `).join("");

      container.querySelectorAll("[data-toggle-read]").forEach(btn => {
        btn.addEventListener("click", () => {
          const item = state.announcements.find(x => x.id === btn.dataset.toggleRead);
          if (item) {
            item.unread = !item.unread;
            saveState();
            renderAll();
          }
        });
      });
    }

    function renderProfile() {
      const p = state.profile;
      document.getElementById("profName").value = p.name;
      document.getElementById("profId").value = p.studentId;
      document.getElementById("profProgram").value = p.program;
      document.getElementById("profYear").value = p.year;
      document.getElementById("profEmail").value = p.email;
      document.getElementById("profBio").value = p.bio;

      document.getElementById("profAvatar").textContent = initials(p.name);
      document.getElementById("profPreviewName").textContent = p.name;
      document.getElementById("profPreviewProgram").textContent = `${p.program} • ${p.year}`;
      document.getElementById("profPreviewBio").textContent = p.bio;
      document.getElementById("profPreviewId").textContent = p.studentId;
      document.getElementById("profPreviewEmail").textContent = p.email;
    }

    // Event Listeners
    document.querySelectorAll(".nav-btn").forEach(btn => {
      btn.addEventListener("click", () => setView(btn.dataset.view));
    });

    document.querySelectorAll("[data-jump]").forEach(btn => {
      btn.addEventListener("click", () => setView(btn.dataset.jump));
    });

    document.getElementById("themeToggle").addEventListener("click", () => {
      state.theme = state.theme === "light" ? "dark" : "light";
      saveState();
      applyTheme();
      showToast(`Switched to ${state.theme} mode`);
    });

    document.querySelectorAll("#scheduleFilters .chip").forEach(chip => {
      chip.addEventListener("click", () => {
        document.querySelectorAll("#scheduleFilters .chip").forEach(c => c.classList.remove("active"));
        chip.classList.add("active");
        scheduleFilter = chip.dataset.day;
        renderSchedule();
      });
    });

    document.querySelectorAll("#announcementFilters .chip").forEach(chip => {
      chip.addEventListener("click", () => {
        document.querySelectorAll("#announcementFilters .chip").forEach(c => c.classList.remove("active"));
        chip.classList.add("active");
        announcementFilter = chip.dataset.cat;
        renderAnnouncements();
      });
    });

    document.getElementById("announcementSearch").addEventListener("input", e => {
      announcementQuery = e.target.value;
      renderAnnouncements();
    });

    document.getElementById("resetGradesBtn").addEventListener("click", () => {
      state.courses.forEach(c => { c.simScore = c.score; });
      saveState();
      renderGrades();
      showToast("Simulated scores reset to current grades");
    });

    document.getElementById("profileForm").addEventListener("submit", e => {
      e.preventDefault();
      state.profile = {
        name: document.getElementById("profName").value.trim() || "Student",
        studentId: document.getElementById("profId").value.trim(),
        program: document.getElementById("profProgram").value.trim(),
        year: document.getElementById("profYear").value,
        email: document.getElementById("profEmail").value.trim(),
        bio: document.getElementById("profBio").value.trim()
      };
      saveState();
      renderAll();
      showToast("Profile saved to browser storage");
    });

    document.getElementById("resetDemoBtn").addEventListener("click", () => {
      state = structuredClone(DEFAULT_STATE);
      saveState();
      renderAll();
      showToast("Demo data restored");
    });

    renderAll();
  </script>
</body>
</html>
