<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=12,20,24&height=200&section=header&text=Sandesh%20Gupta&fontSize=60&fontColor=ffffff&fontAlignY=38&desc=Software%20Developer%20%E2%80%A2%20Java%20%E2%80%A2%20Spring%20Boot%20%E2%80%A2%20Backend%20Engineering&descAlignY=60&descSize=18&animation=fadeIn" width="100%" />

<br/>

[![Typing SVG](https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=22&pause=1000&color=8B5CF6&center=true&vCenter=true&width=700&lines=Java+Developer+%7C+Spring+Boot+%7C+Spring+Security;Building+Secure+REST+APIs+%26+Microservices;JWT+Auth+%7C+OAuth2+%7C+PostgreSQL+%7C+Docker;Clean+Architecture+%7C+Production-Grade+Backend)](https://git.io/typing-svg)

</div>

---

## ⬡ About

```yaml
name:       Sandesh Gupta
alias:      guptaaayansh
role:       Software Developer — Java · Spring Boot · Backend Engineering
location:   Mumbai, India
```

Software developer who builds production-grade systems end to end. I led frontend engineering on **MiloJulo** — a professional and interest-based social networking platform — shipping real-time messaging, WebSocket-driven notifications, geolocation-aware feeds, deep-link routing, and FCM push personalization across both iOS and Android at launch quality. That experience gave me a strong foundation in system design, API contracts, and what it takes to ship to real users.

My current and primary focus is the **Java backend**. I architect stateless REST APIs with Spring Boot 3 and Spring Security 6, design JWT authentication systems with refresh-token rotation and JTI-based revocation, model relational schemas in PostgreSQL, and apply clean layered architecture — domain models, repository interfaces, service abstractions, DTO mapping — consistently across every project. Every backend I build is designed to be maintainable, secure, and production-ready from day one.

**Open To:** Java / Spring Boot backend positions · Software development roles · Backend-heavy product engineering · Teams that value clean architecture and shipped products

---

## ⬡ Tech Stack

<div align="center">

**Languages**

[![Languages](https://skillicons.dev/icons?i=java,python,dart,sql&theme=dark)](https://skillicons.dev)

**Backend & Databases**

[![Backend](https://skillicons.dev/icons?i=spring,hibernate,postgresql,mysql,mongodb&theme=dark)](https://skillicons.dev)

**Cloud, DevOps & Tooling**

[![DevOps](https://skillicons.dev/icons?i=docker,firebase,git,github,linux,postman,idea,gcp&theme=dark)](https://skillicons.dev)

**Platforms & Services**

![Google Cloud](https://img.shields.io/badge/Google%20Cloud-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=flat-square&logo=firebase&logoColor=black)
![Google Play Console](https://img.shields.io/badge/Google%20Play%20Console-414141?style=flat-square&logo=googleplay&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Keycloak](https://img.shields.io/badge/Keycloak-4D4D4D?style=flat-square&logo=keycloak&logoColor=white)
![Swagger](https://img.shields.io/badge/Swagger%20%2F%20OpenAPI-85EA2D?style=flat-square&logo=swagger&logoColor=black)
![Postman](https://img.shields.io/badge/Postman-FF6C37?style=flat-square&logo=postman&logoColor=white)
![IntelliJ IDEA](https://img.shields.io/badge/IntelliJ%20IDEA-000000?style=flat-square&logo=intellijidea&logoColor=white)

</div>

---

## ⬡ Featured Projects

<details>
<summary><strong>TicketHub — Event Ticketing Platform</strong></summary>

<br/>

End-to-end event ticketing system built entirely in Java and Spring Boot, with three distinct user personas — Organizer (creates and manages events), Attendee (purchases QR-backed tickets), and Staff (validates tickets at entry via QR scan). Keycloak handles OIDC identity; Docker Compose orchestrates the full local environment.

| Attribute | Detail |
|:---|:---|
| **Stack** | Java 21 · Spring Boot 3.4 · Spring Security 6 · PostgreSQL · Keycloak · Docker |
| **Architecture** | Layered: Controller → Service → Repository → Entity · MapStruct DTOs · Lombok |
| **Security** | Keycloak OIDC · Spring Security OAuth2 Resource Server · JWT claim extraction |
| **Transactions** | `@Transactional` purchase flow: inventory decrement + ticket creation + QR — atomic |
| **QR Pipeline** | ZXing MultiFormatWriter → UUID string → PNG byte array → stored as `QrCode` entity |
| **Identity Bridge** | `UserProvisioningFilter` auto-creates local DB `User` from JWT on first request |
| **Status Lifecycles** | Event: DRAFT→PUBLISHED→CANCELLED · Ticket: VALID→REDEEMED · QrCode: ACTIVE→USED |
| **Repository** | [![GitHub](https://img.shields.io/badge/guptaaayansh%2Fticket--booking--system-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/guptaaayansh/ticket-booking-system-java-fullstack) |

`UserProvisioningFilter` is the key architectural decision — it bridges the stateless JWT world with the relational DB world so every downstream service operates on a real `User` entity rather than raw JWT claims, eliminating manual user-lookup boilerplate in every controller.

</details>

<details>
<summary><strong>Auth Backend — JWT Authentication Microservice</strong></summary>

<br/>

Production-grade stateless authentication service built with Spring Boot 3 and PostgreSQL. Self-issued JWTs using HMAC-SHA512, full refresh-token rotation with JTI-based revocation audit trails, Google OAuth2 via Spring Security's OAuth2 Client, HTTP-only cookie delivery, and BCrypt password hashing — all documented via SpringDoc OpenAPI.

| Attribute | Detail |
|:---|:---|
| **Stack** | Java 21 · Spring Boot 3.5 · Spring Security 6 · jjwt 0.13 · PostgreSQL |
| **Architecture** | Stateless · `OncePerRequestFilter` JWT validation · RBAC (ADMIN / GUEST) |
| **Security** | HMAC-SHA512 · HTTP-only + Secure + SameSite=Lax cookies · BCrypt |
| **Token Design** | Access (10 min) + Refresh (24 hr) · `typ` claim prevents refresh→access confusion |
| **Rotation** | JTI revocation: `replacedByToken` field builds full refresh-token audit chain in DB |
| **OAuth2** | Google login via Spring OAuth2 Client · `Oauth2SuccessHandler` auto-provisions users |
| **API Docs** | SpringDoc OpenAPI · Swagger UI at `/swagger-ui.html` |
| **Repository** | [![GitHub](https://img.shields.io/badge/guptaaayansh%2Fauth--backend--springboot-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/guptaaayansh/auth-backend-springboot) |

Refresh token resolves from four sources in priority order: HTTP-only cookie → request body → `X-Refresh-Token` header → `Authorization: Bearer` — making it usable from browsers (cookie), mobile apps (header), and Postman/Swagger (body) without changing the endpoint contract.

</details>

<details>
<summary><strong>EzRent — Rental Management Platform</strong></summary>

<br/>

Backend system for managing rental listings, tenant applications, and lease agreements. Built with Spring Boot and a clean service-layer architecture, with JWT-secured endpoints and role-based access for landlords and tenants.

| Attribute | Detail |
|:---|:---|
| **Stack** | Java · Spring Boot · Spring Security · PostgreSQL · JWT |
| **Architecture** | Layered REST API · Service abstractions · JPA repositories |
| **Security** | JWT authentication · Role-based access control |
| **Features** | Listing management · Tenant applications · Lease lifecycle |
| **Repository** | [![GitHub](https://img.shields.io/badge/guptaaayansh%2Fezrent--backend-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/guptaaayansh/ezrent_backend) |

</details>

<details>
<summary><strong>Music Streaming App — Spotify-Inspired Backend</strong></summary>

<br/>

Spotify-inspired music streaming backend with song catalogue management, playlist creation, user library, and streaming endpoint design. Built in Java with Spring Boot following clean REST principles.

| Attribute | Detail |
|:---|:---|
| **Stack** | Java · Spring Boot · PostgreSQL · Spring Security |
| **Architecture** | RESTful API · Entity relationships · Service layer |
| **Features** | Song/album catalogue · Playlists · User library · Search |
| **Security** | JWT auth · User-scoped data access |
| **Repository** | [![GitHub](https://img.shields.io/badge/guptaaayansh%2Fmusic--streaming-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/guptaaayansh) |

</details>

---

## ⬡ Experience

**Freelance Software Developer**
*Independent — Remote*
*Dec 2025 – Present*

Delivering software solutions for clients across backend development and application engineering. Client projects are under NDA; scope covers API development, database design, and custom backend systems.

- Designed and delivered backend systems tailored to individual client requirements
- Managed complete project lifecycle: requirements, architecture, implementation, and handoff
- Maintained ongoing client relationships with iterative delivery

![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)

---

**Software Engineering Intern — Flutter & Backend**
*MiloJulo · Professional & Interest-Based Social Platform — Mumbai*
*Jan 2026 – Oct 2026*

Embedded with the core engineering team on MiloJulo, a production social networking platform targeting simultaneous launch on iOS App Store and Google Play. Contributed across both the Flutter frontend and the NestJS backend throughout the engagement.

**Frontend (Flutter):**
- Owned the frontend for features spanning the full social graph: feed, posts, DMs, group chat, geolocation map, connections, and notifications
- Implemented real-time messaging with Socket.IO — optimistic message inserts, SENDING → CONFIRMED → FAILED state machine with 12s timeout
- Built FCM push notification pipeline: foreground avatar compositing, personalized push copy, deep-link tap routing to the specific in-app target (chat, post, profile, group)
- Engineered deep-link handling for `/p/:id` and `/u/:username` share links with race-safe cold-start resolution, duplicate URI deduplication, and own-profile tab-switch logic
- Designed and shipped the geolocation-aware Nearby feed and live user map with server-side individual pin rendering
- Wired the full auth lifecycle: Google/Apple OAuth2, OTP, JWT refresh interceptor, HTTP-only cookie, session restore on cold start

**Backend (NestJS · PostgreSQL):**
- Contributed to the notifications overhaul: personalized push copy composed server-side, actor enrichment (`name`, `avatarUrl`), like-aggregation math, and FCM retry logic for transient send failures
- Worked on map service: removed server-side clustering in favour of real individual pins at all zoom levels, eliminating the "teleport" visual artifact at cluster threshold crossings
- Contributed to feed distance calculation: integrated viewer's saved Primary Area into `GET /feed/home` so Home posts show distance without requiring live GPS
- Participated in backend PR workflow off the `production` branch — individual PRs per feature, reviewed and merged before deployment

![NestJS](https://img.shields.io/badge/NestJS-E0234E?style=flat-square&logo=nestjs&logoColor=white)
![Flutter](https://img.shields.io/badge/Flutter-02569B?style=flat-square&logo=flutter&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Socket.IO](https://img.shields.io/badge/Socket.IO-010101?style=flat-square&logo=socketdotio&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase%20FCM-FFCA28?style=flat-square&logo=firebase&logoColor=black)
![Google Maps](https://img.shields.io/badge/Google%20Maps%20SDK-4285F4?style=flat-square&logo=googlemaps&logoColor=white)

---

## ⬡ Achievements

<div align="center">

| Recognition | Details |
|:---:|:---|
| 🔐 **Security Architecture** | Designed JWT refresh-token rotation system with full JTI revocation audit chain |
| ⚙️ **Production Backend** | Built stateless Spring Boot auth service reusable across any Java project |
| 🎟️ **Complex Transactions** | Atomic `@Transactional` ticket purchase flow across 3 tables + QR generation |
| 🏗️ **Clean Architecture** | Consistent layered architecture across every project: domain → data → API |
| 🔑 **OAuth2 Integration** | Implemented Google OAuth2 with auto-provisioning via Spring Security OAuth2 Client |
| 🎓 **Academic** | B.Sc. IT, University of Mumbai |

</div>

---

## ⬡ Achievements

<div align="center">

| Recognition | Details |
|:---:|:---|
| 🚀 **Production Launch** | Led frontend engineering on MiloJulo — shipped to both iOS App Store and Google Play |
| 🔐 **Security Architecture** | Designed JWT refresh-token rotation system with full JTI revocation audit chain in DB |
| ⚙️ **Reusable Auth Service** | Built drop-in Spring Boot auth microservice (JWT + Google OAuth2 + PostgreSQL) |
| 🎟️ **Atomic Transactions** | `@Transactional` ticket purchase flow across 3 tables + QR generation — zero partial writes |
| ⚡ **Real-Time Systems** | Socket.IO chat with optimistic updates and SENDING → CONFIRMED → FAILED state machine |
| 🏗️ **Clean Architecture** | Consistent layered architecture across every project: domain → data → service → API |
| 🎓 **Academic** | B.Sc. IT, University of Mumbai |

</div>

---

## ⬡ GitHub Analytics

<div align="center">

<img height="180" src="https://github-readme-stats.vercel.app/api?username=guptaaayansh&show_icons=true&theme=midnight-purple&hide_border=true&bg_color=0D1117&title_color=8B5CF6&icon_color=7C3AED&text_color=C4B5FD&rank_icon=github" />
&nbsp;&nbsp;
<img height="180" src="https://github-readme-stats.vercel.app/api/top-langs/?username=guptaaayansh&layout=compact&theme=midnight-purple&hide_border=true&bg_color=0D1117&title_color=8B5CF6&text_color=C4B5FD&langs_count=6&hide=dart,html,css" />

<br/><br/>

<img src="https://streak-stats.demolab.com?user=guptaaayansh&theme=midnight-purple&hide_border=true&background=0D1117&ring=8B5CF6&fire=7C3AED&currStreakLabel=C4B5FD&sideLabels=C4B5FD&currStreakNum=ffffff&sideNums=ffffff&dates=6B7280" />

</div>

---

## ⬡ Connect

<div align="center">

[![Gmail](https://img.shields.io/badge/sandeshguptasgsg%40gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:sandeshguptasgsg@gmail.com)

</div>

---

<div align="center">

*"First make it work. Then make it right. Then make it fast."*

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=12,20,24&height=120&section=footer&animation=fadeIn" width="100%" />

</div>
