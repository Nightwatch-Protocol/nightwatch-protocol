# Nightwatch Protocol

Nightwatch Protocol is an academic prototype of a real-time asymmetric
multiplayer horror game built using a distributed client-server architecture.

One player assumes the role of a night guard, while the remaining players
control animatronics attempting to reach the security office. The backend
maintains authoritative game state and validates player actions.

## Architecture

The system is divided into independently deployable components:

- **Unity Client:** User interface, player input and game rendering.
- **Auth Service:** User authentication, JWT generation and role management.
- **Matchmaking Service:** Player queue management, role assignment and match creation.
- **Realtime Gateway:** WebSocket connections and real-time command routing.
- **Game Service:** Authoritative match state, gameplay rules and action validation.
- **AWS Infrastructure:** Docker-based service deployment on Amazon EC2.
- **Infrastructure as Code:** Terraform configuration for AWS resource provisioning.

## Repositories

| Component | Responsibility | Repository |
|---|---|---|
| Unity Client | Game interface, rendering and player interaction | [Repository](https://github.com/JuanDeRe/Nightwatch-Protocol-Unity-Client) |
| Realtime Gateway | WebSocket connections and gameplay command routing | [Repository](https://github.com/JuanDeRe/NP-RealtimeGateway) |
| Game Service | Authoritative match state and gameplay rules | [Repository](https://github.com/JuanDeRe/NP-GameService) |
| Matchmaking Service | Player queues, role assignment and match creation | [Repository](https://github.com/JuanDeRe/NP-MatchmakingService) |
| Auth Service | Authentication, JWT generation and user roles | [Repository](https://github.com/JuanDeRe/NP-AuthService) |
| Infrastructure | AWS and Terraform configuration | [Repository](https://github.com/JuanDeRe/NP-Terraform) |

## Communication Flow

1. A user authenticates through the Auth Service.
2. The Unity client sends the player to the Matchmaking Service.
3. The Matchmaking Service groups players and assigns their initial roles.
4. The Matchmaking Service requests the creation of a match from the Game Service.
5. The Unity client establishes a WebSocket connection with the Realtime Gateway.
6. The Realtime Gateway forwards gameplay commands to the Game Service.
7. The Game Service validates each action and produces authoritative game events.
8. The Realtime Gateway sends the resulting events back to connected clients.

## Technologies

- **Backend:** C#, ASP.NET Core and .NET
- **Client:** Unity and C#
- **Communication:** REST APIs, HTTP and WebSockets
- **Testing:** xUnit and automated tests
- **Infrastructure:** Docker, AWS EC2 and Terraform
- **CI/CD:** GitHub Actions
- **Version Control:** Git and GitHub

## Deployment

Backend services were containerized using Docker and deployed on AWS EC2
instances. Terraform was used to define and provision parts of the AWS
infrastructure.

The infrastructure repository documents the resources created and the
deployment assumptions used by the academic prototype.

## Testing and CI

Backend services include automated tests developed with xUnit. GitHub Actions
workflows are used to restore dependencies, build the services and execute
tests.

Examples of validated behavior include:

- Match creation and player role assignment
- Prevention of duplicate matchmaking entries
- Authoritative movement validation
- Invalid movement rejection
- Error handling when dependent services are unavailable
- Core authentication and gameplay behavior

## My Contributions

- Contributed to the distributed architecture design.
- Developed parts of the Game Service and Realtime Gateway.
- Participated in Docker-based deployment on AWS EC2.
- Contributed to Terraform-based infrastructure provisioning.
- Created and reviewed automated tests for backend services.
- Documented service responsibilities and communication flows.

## Project Status

Nightwatch Protocol is an academic prototype developed for a Software
Architecture course.

The core backend services, real-time communication flow, automated tests and
deployment workflow were implemented. Some persistence, scalability,
observability and gameplay features remain experimental or planned.

## Documentation

Additional documentation, including architecture and deployment diagrams,
will be added to this repository.
