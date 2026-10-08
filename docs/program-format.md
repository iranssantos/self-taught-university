# Program file format

A program is a single file that describes a degree: its courses, books, prerequisites, and requirements. Students start a program from the list in the app or load their own file. This page describes the minimum structure every program must meet and the two accepted formats. The complete example is [`programs/bs-mathematics.json`](../programs/bs-mathematics.json).

## Minimum structure

Every program must have the structure described in the [README](../README.md#the-standard):

| Block | Minimum | In the file |
| --- | --- | --- |
| Fixed courses, set by the author | 17 | courses with `kind: "obrig"` |
| Electives offered in the catalog | 11 | courses with `kind: "elet"` |
| Courses offered beyond the fixed ones | 15 | all courses that are not `"obrig"` |
| Courses that can be taken as a seminar | 2 | `"sem"` in `roles` (or `kind: "sem"`) |
| Courses required to complete the program | 32 | `settings.minCourses` |
| Electives required | 11 | `settings.minElectives` |
| Seminars required | 2 | `settings.minSeminars` |
| Hours per course | 170 | `hours` |
| Every course | a code, a name, and a primary textbook (courses that can be seminars choose their texts by topic) | `code`, `name`, a book with `role: "main"` |

Mark as electives (`"elet"`) the courses that belong to the program's field and as free electives (`"opt"`) the others. To let a course be taken as a seminar, give it `roles: ["elet", "sem"]`; taken as a seminar, it still counts as an elective. Students choose how each course counts: any course can be counted as a free elective, electives can also count as electives, and courses with `"sem"` in `roles` can be taken as seminars.

The app checks these rules when a program is loaded, lists anything missing, and does not load a program that fails them. After a program has started, students can add, remove, and edit courses, but the app keeps the minimums: fixed courses cannot be removed, hours cannot go below 170, and the courses, electives, and seminars required cannot be set below 32, 11, and 2. When `minCourses`, `minElectives`, or `minSeminars` are missing, the app uses 32, 11, and 2.

## JSON

```json
{
  "format": "stu-course",
  "version": 1,
  "course": { ... },
  "settings": { ... },
  "books": [ ... ],
  "courses": [ ... ]
}
```

`format` must be `"stu-course"`. `version` is the format version, currently `1`.

### `course`

| Field | Meaning |
| --- | --- |
| `title` | Name of the program, shown at the top of the app |
| `description` | One or two sentences about the program |
| `author` | Who compiled the program |
| `version` | Version of the program (for example `"1.0"`) |
| `basedOn` | The curriculum it is inspired by, if any |
| `language` | Language of the program's texts (for example `"en"`) |
| `handbook` | Optional public link to the program's handbook, shown in the app and on the verification page |

### `settings`

| Field | Meaning | Default |
| --- | --- | --- |
| `monthsPerPeriod` | Length of a term, in months | 4 |
| `periodsPerYear` | Terms per year | 3 |
| `coursesPerPeriod` | Courses planned per term | 2 |
| `minCourses` | Courses required to complete the program (at least 32) | 32 |
| `minElectives` | Electives required (at least 11) | 11 |
| `minSeminars` | Seminars required (at least 2) | 2 |

The student can change any of these in Settings › Schedule.

### `books`

Each book is listed once and referenced by its `id` from any number of courses.

| Field | Meaning |
| --- | --- |
| `id` | Any short identifier, unique in the file |
| `authors`, `title`, `edition`, `publisher`, `year` | Citation details |
| `url` | Optional public page for the book (never a personal file) |

### `courses`

| Field | Meaning |
| --- | --- |
| `number` | Position in the catalog; also used by `prerequisites` |
| `code` | Course code, for example `"MATH 101"` |
| `name` | Course title |
| `kind` | `"obrig"` fixed, `"elet"` elective, `"opt"` free elective (`"sem"` for a course that is always a seminar) |
| `roles` | Optional. `["elet", "sem"]` lets an elective be taken as a seminar |
| `hours` | Nominal hours, at least 170 (a 12-unit MIT subject) |
| `prerequisites` | List of course `number`s |
| `books` | List of `{ "book": id, "role": "main" or "supplementary", "chapters": "1–7" }` |
| `reference` | `{ "name": "MIT 18.06 Linear Algebra", "url": "https://..." }` |
| `minCompleted` | Optional: recommended number of completed courses before this one |

Fixed courses are placed in terms automatically when the program is loaded. All other courses start in the catalog, where the student chooses them.

Regular courses have four problem sets and a cumulative review; courses taken as a seminar have a presentation and a paper. These are created by the app and do not appear in the file.

## CSV

For programs built in a spreadsheet: one row per course, separated by `;` or `,`, with these columns (see [`programs/program-template.csv`](../programs/program-template.csv)):

`number`, `code`, `name`, `type`, `hours`, `prerequisites`, `main_book`, `main_chapters`, `supplementary_book`, `supplementary_chapters`, `reference_name`, `reference_url`

- `type` is `fixed`, `elective`, `free elective`, or `seminar`.
- `prerequisites` are course numbers separated by spaces.
- Books are written as a single citation; rows with the same text share the same book.
- The CSV format has no `roles` or program details, so courses can be seminars only with `type` `seminar`; the requirements default to 32 courses, 11 electives, and 2 seminars. For anything more, write the program as JSON.

## Listing a program on the first screen

The app lists the programs in `programs/index.json`, next to the app:

```json
{
  "programs": [
    {
      "file": "bs-mathematics.json",
      "title": "Bachelor of Science in Mathematics",
      "description": "One or two sentences.",
      "courses": 32,
      "hours": 5440,
      "basedOn": "MIT Course 18 (Mathematics)",
      "handbook": "docs/handbook.pdf"
    }
  ]
}
```

`file` is the program's file name inside `programs/`; `handbook` is an optional link to its handbook. The other fields are what the list shows.

## Good practice

- Say "inspired by" when a program follows another institution's curriculum, and do not suggest any affiliation.
- Link to reference courses and book pages; never to copies of copyrighted books.
- Check chapters against a specific edition, and name that edition.
