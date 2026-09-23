# RaceDay — Event Management System

---

## Project Overview

RaceDay is a full-stack web-based event management system for the South African road running, walking, and cycling community. It allows Event Organisers to create and manage events, categories, and results, while Participants can browse events, enter events, and track their personal performance history.

This repository contains **Part 1**: the ERD, API endpoint plan, and SQL database script. No application code is written in this part.

---

# Roles
 Organiser -  Creates, edits, and deletes events; manages categories; captures results; views all enrolments. |
 Participant - Creates an account; browses events; enters events by selecting a category; views own enrolments and results. |

---
# Setup Instructions

### Prerequisites
- SQL Server (Express/Developer)
- SQL Server Management Studio (SSMS)
- Git and a GitHub account

### Running the SQL Script
1. Open **SSMS** and connect to your SQL Server instance.
2. Open `docs/RaceDay_Database_Script.sql`.
3. Press **F5** to execute.
4. The script creates `RaceDayDB`, all 8 tables, seed data, and runs verification queries.


Database Schema (8 Entities)

1. **User** | Stores both Organisers and Participants via `Role` discriminator |
2. **Event** | Events created by Organisers |
3. **Category** | Age/distance categories for each event |
4. **Enrolment** | Links Participants to Events and Categories |
5. **Result** | Finish times and positions (one-to-one with Enrolment) |
6. **EventOrganiser** | Many-to-many junction for co-organisers |
7. **PasswordResetToken** | Secure password reset tokens |
8. **AuditLog** | Security and debugging audit trail |

 Key Relationships

 User (Organiser) → Event | 1 : M |
 Event → Category | 1 : M |
 User (Participant) → Enrolment | 1 : M |
 Event → Enrolment | 1 : M |
 Category → Enrolment | 1 : M |
 Enrolment → Result | 1 : 1 |
 Event ↔ User (Organiser) | M : N |

---

 YouTube Video


> 5–7 minute unlisted video explaining the ERD, endpoint plan, and demonstrating the SQL script running live in SSMS.

---

References

Fielding, R.T. 2000. *Architectural styles and the design of network-based software architectures*. Ph.D. dissertation. University of California, Irvine.

Fowler, M. 2002. *Patterns of enterprise application architecture*. Boston: Addison-Wesley.

GitHub. 2025. *GitHub Actions documentation*. [Online]. Available at: https://docs.github.com/en/actions [Accessed 20 September 2026].

Microsoft. 2025. *RESTful web API design best practices*. [Online]. Available at: https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design [Accessed 21 September 2026].

Microsoft. 2025. *SQL Server documentation*. [Online]. Available at: https://learn.microsoft.com/en-us/sql/ [Accessed 20 September 2026].

The Independent Institute of Education. 2026. *Programming 2B (PROG6212/w) Portfolio of Evidence*. Johannesburg: IIE.
