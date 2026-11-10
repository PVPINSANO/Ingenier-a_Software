```mermaid
graph TD
 subgraph ClientNode [Nodo Cliente (Navegador Web / App Móvil)]
 UI ["Interfaz de Usuario SATE (HTML5 / Bootstrap)"]
 end
 subgraph GitHubNode [Nodo CI/CD (GitHub Actions)]
 Runner ["Runner Linux (Maven + JDK 17 + JUnit 5)"]
 end
 subgraph AppServerNode [Nodo Servidor de Aplicación (Staging - Cloud/Docker)]
 MVC ["Controladores & Servicios (SATE Core Engine)"]
 end
 subgraph DBNode [Nodo Servidor de Base de Datos]
 DB [("PostgreSQL / MySQL Data Store")]
 end
 UI -->|HTTPS / REST API| MVC
 Runner -->|Automated Deployment / SSH| MVC
 MVC -->|JDBC / SQL Connection| DB
```
```mermaid
architecture-beta
    group cliente(cloud)[Cliente / Dispositivo]
    group github(cloud)[Entorno DevOps CI/CD]
    group servidor(server)[Servidor de Aplicación - Staging]
    group bd(database)[Servidor de Datos]
    service browser(internet) in cliente [Navegador Web / App]
    service runner(server) in github [GitHub Actions Runner]
    service app(server) in servidor [SATE Application Server - Java 17 Spring]
    service postgres(database) in bd [PostgreSQL Database Engine]
    browser:R -- L:app
    runner:B -- T:app
    app:R -- L:postgres
```
