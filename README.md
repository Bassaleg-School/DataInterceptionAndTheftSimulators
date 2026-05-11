# DataInterceptionAndTheftSimulators

Live demo: https://h-arnold.github.io/DataInterceptionAndTheftSimulators/

A collection of standalone web pages that simulate common data interception and session-theft attacks for classroom use. These interactive activities are designed to support teaching and learning for the WJEC GCSE Computer Science specification (2025).

## Activities

- **Packet Sniffing** (`PacketSniffing.html`) — Simulates how unencrypted network traffic can be intercepted to reveal sensitive data and credentials. Includes guided tasks and student questions. 🔍
- **Session Hijacking** (`SessionHijacking.html`) — Demonstrates how attackers can steal or reuse session tokens to impersonate users. 🧩
- **Man-in-the-Middle (MiTM) Simulation** (`MitMSimulation.html`) — Shows interception and manipulation of traffic between two parties. 🛡️
- **Index / Landing Page** (`index.html`) — Entry point linking to each activity.

## Teacher Notes

Detailed lesson plans, worksheets and answers are included in the `TeacherNotes/` folder:
- `TeacherNotes/MitMActivity.md`
- `TeacherNotes/PacketSniffingActivity.md`
- `TeacherNotes/SessionHijackingActivity.md`

## Usage

- **Live**: Visit the hosted site above to try the activities directly. ✅
- **Local**: Open `index.html` in a browser, or serve locally with a simple HTTP server (for example: `python3 -m http.server 8000`). No special dependencies required—works in modern browsers. 🔧

## Audience & Purpose

This repository is aimed at teachers and students preparing for GCSE-level topics in network security, offering classroom-friendly simulations and supporting materials to reinforce learning.

## Contributing

Contributions, fixes or suggestions are welcome—please open issues or submit pull requests. 💡

## License

See the `LICENSE` file for license information.
