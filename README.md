<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=12,20,24&height=200&section=header&text=Sandesh%20Gupta&fontSize=60&fontColor=ffffff&fontAlignY=38&desc=Software%20Developer&descAlignY=60&descSize=20&animation=fadeIn" width="100%" />

<br/>

[![Typing SVG](https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=19&duration=2800&pause=900&color=8B5CF6&center=true&vCenter=true&repeat=true&width=700&height=45&lines=Building+backends+that+are+secure+and+production-ready.;Turning+good+architecture+into+shipped+products.;I+write+code+that+is+correct%2C+clean%2C+and+built+to+last.)](https://git.io/typing-svg)

</div>

---

## ⬡ About

```yaml
name:       Sandesh Gupta
alias:      guptaaayansh
role:       Software Developer — Java · Spring Boot · Backend Engineering
location:   Mumbai, India
```

Java software developer with hands-on experience building and shipping production systems. I design secure REST APIs, architect clean layered backends, and take ownership of features from database schema through to deployment.

My core stack is **Java + Spring Boot** — Spring Security, JPA/Hibernate, PostgreSQL, JWT authentication, OAuth2. I care about writing code that is correct, maintainable, and built to last — not just code that compiles.

Beyond backend, I have real production experience on the frontend side through internship work, which gives me a strong understanding of the full system — API contracts, data flow, and how backend decisions affect the product.

**Open To:** Java / Spring Boot roles · Backend engineering · Software development positions

---

## ⬡ Tech Stack

<div align="center">

**Languages**

[![Languages](https://skillicons.dev/icons?i=java,python,dart,sql&theme=dark)](https://skillicons.dev)

**Backend & Databases**

[![Backend](https://skillicons.dev/icons?i=spring,hibernate,postgresql,mysql,mongodb&theme=dark)](https://skillicons.dev)

**Mobile**

[![Mobile](https://skillicons.dev/icons?i=flutter,androidstudio&theme=dark)](https://skillicons.dev)

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

**Software Engineering Intern** · *MiloJulo, Mumbai · Jan 2026 – Oct 2026*

Contributed across Flutter frontend and NestJS backend on a production social networking platform shipped to both App Stores.

- Built real-time DM & group chat (Socket.IO), FCM push notifications, geolocation map, and full auth lifecycle
- Worked on backend: notifications overhaul, map pin rendering, feed distance calculation
- Shipped features end-to-end across the full social graph: feed, posts, connections, groups, DMs

![NestJS](https://img.shields.io/badge/NestJS-E0234E?style=flat-square&logo=nestjs&logoColor=white)
![Flutter](https://img.shields.io/badge/Flutter-02569B?style=flat-square&logo=flutter&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=flat-square&logo=firebase&logoColor=black)

---

**Freelance Software Developer** · *Dec 2025 – Present*

- Delivering backend systems and APIs for clients under NDA
- Full project lifecycle: requirements → architecture → delivery

![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)

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
