# Backend / Server

1. ### Backend Architecture Guide {#backend-architecture-guide}

        1. #### Introduction and System Overview {#introduction-and-system-overview}

This document serves as a comprehensive guide to the architecture, setup, and best practices of the eCozy backend application.  
The backend is the core of a **smart heating IoT system**, tailored to interact with:

* **Thermostats:** Physical embedded devices.  
* **Central Units:** Hubs or gateways managing multiple thermostats.  
* **User Interfaces:** Mobile/Web apps for defining heating algorithms and scenarios.

Built with **NestJS** (Node.js \+ TypeScript), the application adheres to **Hexagonal Architecture** concepts within a **Modular** structure. This ensures scalability, maintainability, and strict separation of business logic from infrastructure concerns.

2. #### Technology Stack {#technology-stack}

| Layer | Technology |
| :---- | :---- |
| **Framework** | NestJS (TypeScript) |
| **Database** | PostgreSQL |
| **ORM** | TypeORM |
| **Auth** | JWT \+ Google/Apple/Amazon OAuth |
| **Email** | Maildev (Dev) \+ Nodemailer |
| **Environment** | Docker \+ Docker Compose |
| **Localization** | i18n support |

   3. #### High-Level Architecture (Macro-Structure) {#high-level-architecture-(macro-structure)}

The project uses a **Module-Oriented Structure**. Each business domain is isolated as a self-contained NestJS module in the src/ directory.

**Core Domain Modules**

| Folder | Purpose |
| :---- | :---- |
| auth, auth-google, auth-apple | User authentication (JWT, OAuth strategies). |
| users, me, roles | User management, profiles, and RBAC permissions. |
| central-units\* | Management of hardware hubs/gateways. |
| thermostats\* | Management of individual devices, logs, and sessions. |
| heating-algorithm | Core domain logic for smart heating control. |
| scenarios | User-defined sequences or triggers (e.g., "Away Mode"). |
| notifications, mailer | Email alerts and user messaging. |
| files, rooms, locations | Spatial organization and file resources. |

*Note: Modules marked with (*) involve heavy interaction with embedded devices.\*

4. #### Module Internal Architecture (Micro-Structure) {#module-internal-architecture-(micro-structure)}

To ensure the **Separation of Concerns** dictated by Hexagonal Architecture (Ports and Adapters), individual modules—especially complex ones like heating-algorithm or users—should follow this internal directory structure:  
**Directory Structure:**

* src/module-name/  
  * domain/ (Pure Business Logic)  
    * \[ENTITY\].ts (Core business entities, no infra dependencies)  
  * dto/ (Data Transfer Objects)  
    * create.dto.ts  
    * update.dto.ts  
  * infrastructure/ (Implementation details)  
    * persistence/  
      * relational/  
        * entities/ (Database specific entities/TypeORM)  
        * mappers/ (Converts DB Entity \<-\> Domain Entity)  
        * repositories/ (Implementation of the repository interfaces)  
  * controller.ts (API Endpoints/Adapters)  
  * module.ts (Dependency Injection wiring)  
  * service.ts (Orchestration of logic)

**Design Principles**

* **Domain Layer:** Represents core business entities. It should *never* depend on the database or HTTP layers.  
* **Ports (Interfaces):** Defined in the domain/service layer.  
* **Adapters (Infrastructure):** Implementations of those interfaces (e.g., a TypeORM repository).

  2. ### Implementation Best Practices {#implementation-best-practices}

     1. #### Repository Design {#repository-design}

Repositories should focus on **single-responsibility methods**. Avoid overly generic implementations (like find(condition)) that leak database logic into the business layer.  
**❌ Avoid Generic Methods:**  
TypeScript  
async find(condition: UniversalConditionInterface): Promise\<User\> { ... }

**✅ Use Specific Intent Methods:**  
TypeScript  
async findByEmail(email: string): Promise\<User\> { ... }  
async findByRoles(roles: string\[\]): Promise\<User\> { ... }

2. #### DTO and Validation {#dto-and-validation}

All inputs must be strongly typed and validated using class-validator.  
TypeScript  
export class CreateUserDto {  
  @IsEmail()  
  email: string;

  @IsString()  
  password: string;  
}

3. #### Serialization (Role-Based Access) {#serialization-(role-based-access)}

The application uses class-transformer. Sensitive data is stripped out globally unless explicitly exposed for specific roles (e.g., Admins).  
TypeScript  
// Controller  
@SerializeOptions({ groups: \['admin'\] })  
@Get(':id')  
findOne(...) { ... }

// Entity  
@Entity()  
export class User {  
  @Expose({ groups: \['admin'\] }) // Only visible if 'admin' group is active  
  email: string;  
}

3. ### Authentication and Device Communication {#authentication-and-device-communication}

   1. #### User Authentification {#user-authentification}

* **Primary:** Email/Password or OAuth (Google/Apple/Amazon).  
* **Session:** Stateless JWT (JSON Web Tokens).  
* **Refresh Flow:** When Access Token expires, use the Refresh Token at /auth/refresh to rotate credentials.

  2. #### Embedded Device Communication {#embedded-device-communication}

The backend manages sessions for IoT devices:

* **Auth:** Devices authenticate via central-units-auth.  
* **Session:** Established via central-units-session.  
* **Logic:** User scenarios dispatch commands; the heating-algorithm processes telemetry logs.

  4. ### Setup and Deployment {#setup-and-deployment}

**Quick Start**  
Bash  
\# Start infrastructure (DB, Maildev)  
docker compose up \-d

**Full Development Setup**  
**Clone & Config:**  
Bash  
git clone \<repository\_url\>  
cp env-example .env  
\# Set DATABASE\_HOST=localhost, MAIL\_HOST=localhost

1. 

**Install & Migrate:**  
Bash  
npm install  
npm run migration:run  
npm run seed:run

2. 

**Run:**  
Bash  
npm run start:dev  
\# API available at: http://localhost:3000  
\# Maildev available at: http://localhost:1080 (usually)

5. ### Engineering Notes and Future Roadmap {#engineering-notes-and-future-roadmap}

* **Architecture:** The modular structure is enterprise-grade.  
* **Scalability:** The separation of heating-algorithm allows for future implementation of ML-based optimizations without rewriting the API layer.  
* **Connectivity:** Current session handling sets a strong foundation for a future upgrade to **MQTT/WebSockets** for real-time bi-directional control.

  6. ### Quick Links {#quick-links}

* API Documentation (Swagger): [http://localhost:3000/docs](http://localhost:3000/docs)  
* Database Client (Adminer): [http://localhost:8080](http://localhost:8080)  
* Email Testing (MailDev): [http://localhost:1080](http://localhost:1080)
