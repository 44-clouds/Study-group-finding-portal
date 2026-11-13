# Peer Study Group Finder

**Assignment 3: End-to-End Portal Design** | FAST - National University, Lahore

| | |
|---|---|
| Team member 1 | [Maham Waqas], [25l-5225] |
| Team member 2 | [Khadija Amir], [25l-5110] |
| Course | [Programming for Business] |

## Description

Peer Study Group Finder is a console-based portal written in Python that helps university
students form study groups for the subjects they are taking. Students register a profile
(programme, semester, subjects with grades and interest level, availability, and optional
mentor details), find open groups that match their subjects, and agree on a **time, location
and price** through a counter-offer process:

1. A student creates a group, which records the first proposal.
2. Any member can **accept** the proposal or **counter** it with a different time, location or price.
3. The group is **confirmed** only when every member has accepted the current proposal.

The portal is backend-only, with an interactive terminal menu. Data is stored in JSON files
and persists between runs.

## Features

- Registration and login with input validation (unique user ID, password length, CGPA range, etc.)
- Student profiles: subjects, grades, interest (`intrigued` / `marks` / `both`), availability slots
- Mentors: optional charge (0 = free) and proof of knowledge (project, midterm result, previous record)
- Study groups: create, find matches by subject, join
- Negotiation: propose, counter and accept time, location and price, with a stored history
- Reports: groups per subject, confirmed vs open groups, mentor count, average mentor charge, average CGPA
- Error handling for invalid input and file problems (the portal does not crash)

## Requirements

- Python 3.8 or later
- Jupyter Notebook or JupyterLab (or VS Code with the Jupyter extension)
- No third-party libraries are needed (only the built-in `json` and `os` modules)

## How to run

1. Clone or download this repository.
2. Open `Assignment3_Portal.ipynb` in Jupyter Notebook.
3. Run all cells from top to bottom (`Kernel > Restart & Run All`). Sections 1 to 8 define the
   functions; section 9 shows six sample test runs using prepared inputs.
4. To use the portal yourself, remove the `#` in the last code cell (`main()`) and run it.

The first run creates `users.json` and `groups.json` automatically. Section 9 begins by deleting
old demo data, so remove that cell if you want to keep your own records.

## Files

| File | Purpose |
|---|---|
| `Assignment3_Portal.ipynb` | All code, explanations and sample test runs |
| `users.json` | User records (created and updated by the portal) |
| `groups.json` | Study-group records, including negotiation history |
| `README.md` | This file |

## Data design (summary)

- **User:** `user_id`, `password`, `name`, `gender`, `cgpa`, `program`, `semester`, `subjects`
  (list of `name` / `grade` / `interest`), `availability`, `can_mentor`, `charges`, `proof`
- **Group:** `group_id`, `subject`, `creator_id`, `members` (user IDs), `max_members`, `mentor_id`,
  `time`, `location`, `price`, `status`, `accepted_by`, `history`

A group refers to its members by `user_id` only, so each student's details are stored once.

## Sample accounts (created by the demo in section 9)

| User ID | Password | Role |
|---|---|---|
| `ali123` | `pass1234` | Mentor |
| `sara01` | `sara2026` | Learner |
| `hamza9` | `hamza2026` | Learner |

## Limitations

Passwords are stored as plain text (a production system would hash them). Real-time chat,
online payments and file uploads are outside the scope of this project.
