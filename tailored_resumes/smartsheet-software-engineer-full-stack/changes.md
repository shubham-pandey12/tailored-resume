# Changes from Master Resume — Smartsheet | Software Engineer - Full Stack

**Prepared:** November 5, 2026  
**Target Role:** Software Engineer - Full Stack (Platform Team)  
**Target Company:** Smartsheet  

---

## 1. Master Resume Hash Verification

- **Master resume path:** `/Users/shubhampandey/Desktop/SP/job-hunter/resume/resume.tex`
- **Initial SHA-256 hash:** `9b7e442a01f15ce5ab3f71c9e4b279b94c52f467ed4080a8a1876d79a6426b33`
- **Current SHA-256 hash:** `9b7e442a01f15ce5ab3f71c9e4b279b94c52f467ed4080a8a1876d79a6426b33`
- **Verification status:** ✅ Identical — master `resume.tex` is completely untouched.

---

## 2. LaTeX Preamble Adjustments

- `\addtolength{\topmargin}{-.70in}` (changed from `-.45in` in master per Rule 3 to ensure an exact 1-page fit with balanced margins).
- All other margin settings (`\oddsidemargin`, `\evensidemargin`, `\textwidth`, `\textheight`), document class, packages, and custom command definitions were copied verbatim from master.

---

## 3. Skills Summary Changes

In accordance with Rule 1's decision table (`Java only (no Node.js) → Java — replace Node.js references with Java`):

| Row | Master Resume | Tailored for Smartsheet | Specific JD Rationale |
|---|---|---|---|
| **Backend** | `Java, Node.js, Express.js, Python, REST APIs, GraphQL, Microservices` | `Java, Spring Boot, Microservices, REST APIs, Object-Oriented Design (OOD)` | Replaced Node.js/Python with Java/Spring Boot; added Object-Oriented Design (OOD) and Microservices to reflect core JD requirements. |
| **Frontend** | `React.js, Next.js, TypeScript, JavaScript, Redux` | `React.js, JavaScript, TypeScript, HTML5, CSS3, CSS Pre-processors (Sass/SCSS), Redux` | Explicitly added HTML5, CSS3, and CSS Pre-processors (Sass/SCSS) as required by the JD. |
| **Databases** | `SQL, MySQL, MongoDB, Redis` | `MySQL, DynamoDB, MongoDB, Redis, Relational & Non-Relational Databases` | Added DynamoDB (Nice-to-Have in JD) and explicitly framed relational (MySQL) and non-relational database experience. |
| **Infrastructure** | `AWS (EC2, S3, ECS, CloudFront), Docker, Jenkins, CI/CD, Git` | `AWS (EC2, S3, ECS), Docker, Kubernetes (k8s), HashiCorp, Linux (tcpdump, strace), Git` | Added Kubernetes (k8s), HashiCorp, and Linux debugging commands (`tcpdump`, `strace`) per JD preferences. |
| **Testing & AI** | `Jest, Unit Testing, Integration Testing, Automated Testing` | `JUnit, Jest, Unit Testing, Integration Testing, QA, Defect Resolution, AI Tools (Copilot)` | Added JUnit, Quality Assurance (QA), Defect Resolution, and AI Tools to match JD's focus on quality lifecycle and AI enablement. |

---

## 4. Work Experience Bullets Changes

All roles, dates, companies, and metrics were preserved. Number of bullets per role remains strictly identical (4 + 3 + 2 + 1 = 10 bullets):

### Moresand Technologies (4 bullets)
- **Bullet 1:** Highlighted scalable high-availability architecture, Java Full Stack, React.js, Object-Oriented design, and microservice boundaries. Maintained 50% onboarding reduction metric.
- **Bullet 2:** Focused on REST APIs and schema design across MySQL (relational) and DynamoDB (NoSQL), emphasizing full lifecycle data contracts from concept to release.
- **Bullet 3:** Framed modular UI component library in React.js, JavaScript, and CSS pre-processors (SCSS) with Redis caching. Maintained 50% dev effort reduction.
- **Bullet 4:** Weaved in Linux debugging commands (`tcpdump`, `strace`), systems engineering collaboration, and CI/CD quality assurance for 99.9% uptime.

### MAQ Software (3 bullets)
- **Bullet 1:** Tailored to production Java backend microservice and AI assistant orchestration layer, emphasizing Object-Oriented design principles and 28% prompt accuracy improvement.
- **Bullet 2:** Explicitly incorporated JD responsibility on utilizing AI tools (GitHub Copilot, Cursor) across coding, defect resolution, and troubleshooting, plus coaching engineers on AI enablement.
- **Bullet 3:** Highlighted responsive React.js + TypeScript UI styled with CSS pre-processors connected to Java REST APIs and AWS cloud infrastructure.

### Techolution (2 bullets)
- **Bullet 1:** Positioned full-stack feature delivery across Java microservices and React.js frontends, highlighting quality assurance, defect resolution, and 90% test coverage.
- **Bullet 2:** Weaved in Docker, Kubernetes (k8s), and HashiCorp orchestration tools on AWS. Maintained 60% deployment reduction metric.

### GeeksForGeeks (1 bullet)
- **Bullet 1:** Re-anchored to HTML, CSS, CSS pre-processors (Sass), JavaScript, and React.js modular components, maintaining 30% engagement and 40% performance gains.

---

## 5. Frozen Sections (Verbatim from Master)

Per Rule 2, the following sections remain 100% identical to the master resume:
- **Header:** Full contact details, email, phone, GitHub, LinkedIn, Portfolio.
- **Education:** IIIT Vadodara — Bachelor of Technology in Information Technology.
- **Projects:** Single project (WebHealth) copied verbatim without modification; Mobivax kept commented out.
- **Achievements:** HACKIIITV 2019 Best Idea Award copied verbatim.

