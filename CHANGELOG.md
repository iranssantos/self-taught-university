# Changelog

## 1.0 — October 2026

First public release.

- App installed on Android, iPhone, and computers, working offline: Today, Courses, Calendar, Transcript, and Settings. In a browser, the page presents the app and offers installation.
- Programs follow a minimum structure modeled on an MIT bachelor's degree (17 fixed courses, 11 electives, free electives up to 32 courses of 170 hours, and 2 seminars), checked when a program is loaded and kept when it is edited. The student adds each catalog course as an elective, a free elective, or a seminar, and can switch it later, while its group is not complete; a course taken as a seminar keeps counting in its block. Published programs not yet started are listed in Settings, with a notice when a new one appears.
- Starts empty: the first screen lists the programs published with the app and also loads a student's own program from a file or a link. Included program: Bachelor of Science in Mathematics (`programs/bs-mathematics.json`), modeled on MIT Course 18 — 17 fixed courses (the nine subjects every MIT mathematics major takes, two more in mathematics, and six in computing with mathematical content), 11 electives, 4 free electives, and 2 seminars, 32 courses of 170 nominal hours each.
- Getting-started guidance after a program is loaded, and an in-app Guide covering every screen and feature.
- Courses with codes, prerequisites, primary and supplementary texts with chapters, and reference courses.
- Flexible terms: due dates computed from each course's start, with later terms moving as the student finishes early or late. After the first year, each term keeps a slot for a course the student chooses.
- Problem sets and cumulative review per course; presentation and paper for seminars; work submitted as links to the student's own files.
- Several programs per device; import and export of programs as JSON or CSV ([format](docs/program-format.md)).
- All data stays on the device. Configuration file to back up and restore everything, with a reminder when there are unsaved changes; calendar export (.ics).
- Verification page generator, with the student's name, start and finish dates, curriculum and diploma links, and a gradebook with the links the student recorded to their work.
- Light, dark, or system appearance.
- Program Handbook (`docs/handbook.md`, `docs/handbook.pdf`).
