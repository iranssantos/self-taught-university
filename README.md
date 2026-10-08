# Self-Taught University

A free app for studying a complete undergraduate program on your own, and for keeping the record that proves it.

Self-Taught University is not a course platform: it provides no lessons, problems, or grades. It is a tool for students who take charge of their own degree. You choose a program, study from its books and reference courses, prepare and solve your own assignments, check them, and keep the files. The app organizes the program, keeps a minimum protocol for every course, and records your work: it plans your terms, tracks the books, reference courses, and due dates of each course, logs your study hours, builds your transcript, and generates a page that lets anyone you choose see the work behind each course. It runs on Android, iPhone, and computers, offline, and everything stays on your device.

## How it works

**You do:**

- Prepare each assignment from the course's books and reference course (for example, an MIT OpenCourseWare course), solve it, check it, and save it as a PDF.
- Store your files wherever you choose (Google Drive, for example), make each link public so that anyone with it can open the file, and paste the link in the app.
- Create your own diploma, publish it the same way, and paste its link in the app.
- Download your verification page from the app and publish it yourself, on any web host (GitHub Pages, for example).
- Save your configuration file from time to time and keep it safe.

**The app does:**

- Plans your terms and due dates, keeps the protocol of every course (four problem sets and a cumulative review, or a recorded presentation and a paper for a seminar), and records the links you paste, your dates, and your study hours.
- Builds your transcript and the verification page file, listing every course with the links you recorded.
- It does not store, check, or publish any file, and it cannot tell whether a link is public. A course counts as completed only when every assignment has a link.

Your credibility comes from the work you make public: anyone you share your verification page with can open each file and examine it.

## The standard

Every program in the app has the same minimum structure:

| Block | Minimum | Who decides |
| --- | --- | --- |
| Fixed courses | 17 | The program's author; the same for every student |
| Electives | 11 | The student, from the program's catalog of electives |
| Free electives | the rest, up to 32 | The student, from the whole catalog: any course can be counted as a free elective |
| Seminars | 2, counted within the electives or free electives | The student, among courses that allow it |
| **Total** | **32 courses of at least 170 hours each** | |

- **Seminars** are assessed by a recorded presentation and an expository paper instead of problem sets. A course taken as a seminar keeps counting in its block, and a course that allows it but is not taken as a seminar counts normally, so no course is wasted.
- **How each course counts** is the student's choice: when adding a course from the catalog, the student picks elective, free elective, or seminar, and can switch later. Each option disappears once its group is complete.
- **170 hours** per course is about 12 hours of study a week over a 14-week term.
- Every course has a code, a name, a primary textbook, and preferably a reference course.

**To build your own program,** follow this protocol:

1. Set **17 fixed courses**.
2. Offer a catalog with at least **11 electives** and enough other courses to reach **15 beyond the fixed ones** (more is better, so that students have a choice), including at least **2 that can be taken as a seminar**.
3. Require at least **32 courses** to complete the program, with at least **11 electives** and **2 seminars**.
4. Give every course at least **170 hours**, a code, a name, and a primary textbook, and preferably a reference course.

A program that does not meet this structure is not accepted, and once a program has started, students can add or remove courses only as long as the minimums still hold. The file format is in [docs/program-format.md](docs/program-format.md).

## Install

The app is installed from its page (the address in the **About** panel of this repository) and runs once installed:

- **Android:** open the page in Chrome and tap **Install app**, or use the menu ⋮ › **Install app** (or **Add to Home screen**). The app appears among your installed apps.
- **iPhone and iPad:** open the page in Safari and tap **Share** › **Add to Home Screen**.
- **Computer:** open the page in Chrome or Edge and click **Install app**, or the install icon in the address bar.

Firefox on computers and browsers other than Safari on iPhone cannot install web apps; use one of the browsers above. Installed copies update themselves when a new version is published here.

## Getting started

1. Open the installed app and choose a program from the list, or load your own.
2. Follow the *Getting started* box on the Today screen: set your start date, add your name, and tap **Start** when you begin a course.
3. The **Guide** (top right) explains every screen and feature.

## Your data

Everything you enter stays on your device. Nothing is sent to this repository, to GitHub, or to anyone else.

- **Back up** with **Save configuration** (in Settings, or the mark at the top of the app, which turns into an orange dot when there are unsaved changes). It downloads one file with all your programs, progress, and notes; keep it somewhere safe.
- **Restore** on another device with **Load configuration**.
- **Your files** (solutions, books) stay wherever you keep them; the app only stores links to them.

Uninstalling the app or clearing its data erases what is on the device. The configuration file is what brings it back.

## Programs

The programs listed in the app are in `programs/`:

- **Bachelor of Science in Mathematics** (`programs/bs-mathematics.json`), in the structure of MIT Course 18: 17 fixed courses (9 in mathematics, 2 in physics, and 6 in computing with mathematical content), 11 electives, 4 free electives, and 2 seminars. Its [Program Handbook](docs/handbook.md) ([PDF](docs/handbook.pdf)) describes the requirements, every course, and how work is assessed. It is *inspired by* MIT Course 18; it is not affiliated with or endorsed by MIT.

New programs published here appear in the app under **Settings › Programs**, and the app tells you once when a new one is available.

You can also load a program of your own, as a JSON or CSV file, provided it meets the standard above. The format is described in [docs/program-format.md](docs/program-format.md).

Self-Taught University is not an accredited institution, and completing a program does not confer an accredited degree. Its credibility rests on the work each student makes public.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The app (HTML, CSS, and JavaScript in one file) |
| `sw.js` | Offline support |
| `manifest.webmanifest`, `favicon.png`, `icon-192.png`, `icon-512.png`, `icon-maskable-512.png`, `apple-touch-icon.png` | Installation on Android, iPhone, and computers |
| `logo.png` | Self-Taught University logo, with a transparent background, used by the app and verification pages |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are |
| `programs/index.json` | Programs listed in the app |
| `programs/bs-mathematics.json` | Bachelor of Science in Mathematics |
| `programs/program-template.csv` | Spreadsheet template for a program |
| `docs/program-format.md` | Program file format and minimum structure |
| `docs/handbook.md`, `docs/handbook.pdf` | Program Handbook of the mathematics program |
| `CHANGELOG.md` | Release notes |
| `LICENSE`, `LICENSE-CONTENT.txt` | Licenses |

## License

- **Code** (`index.html`, `sw.js`, `manifest.webmanifest`): [GNU General Public License v3.0](LICENSE).
- **Content** (programs, handbook, documentation, and logo): [Creative Commons Attribution-NonCommercial-ShareAlike 4.0](LICENSE-CONTENT.txt).

Textbooks and reference courses belong to their authors and institutions; programs only cite and link to them.
