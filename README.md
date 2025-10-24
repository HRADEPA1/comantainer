# comantainer
Container web ui manager. Manage Podman, Docker containers, images, repositories, volumes, networks.

# Container
The implementation of the manager is deployed as container with Podman, Docker.

## Server
One container thats run in linux and have configuration, user mangement with RBAC, enviroment management (connected clients). This container contain Backend, Database, Frontend.

## Client
Onother container that runs on other enviroments that works like remote client. This client can manage Podman, Docker.
When configure this container set the server and port for connect to the backend. 

#Backend
Written in Python and use connection to Podman, Docker REST api.
When HTTPS can generate and maintain qualified certificate for specified domain from Lets Encrypt. For generate and maintain certificates use DNS challenge (Azure, CloudFlare).
The configuration data are stored in MariaDB database.
Provide CRUD Rest API for:
- users
- groups
- roles
- enviroments
- registries
- notifications
- logs
- settings
  - authentication (Local, LDAP, OAuth, Active Directory)


# Web UI
Written in VUE 3 and communicate with backend over HTTP/HTTPS. When user is authenticated the dashboard is displayed.

## Menu
- Users
  - Users
  - Groups
  - Roles
- Enviroments
  - New
  - Edit
  - Delete
  - Detail -> display enviroment dashboard
  - Manage access
- Registries
  - New
  - Edit
  - Delete  
- Account
  - Theme (Light, Dark, System)
  - Change password
  - Access token (use for backend Rest API)
- Logs
  - Export
  - Remote log server
- Notifications
  - Rules for notifications send to group, user by e-mail 
- Logout


## Dashboard
List of the enviroments where information:
- Name
- Address
- Type (Podman, Docker, Cubernetes)
- Count of containers (total, running, stopped)
- Count of stacks
- Volumes (count, total size)
- Images (count, total size)
- CPUs
- RAM
- Status
- Version

## Enviroment dashboard
- The dashboard defined above
- Stacks - stack defined with docker compose yaml. Can be defined internaly with editor o can be defined remotely by docker, podman commands.
- Containers - List of containers
  - Name
  - State
  - Actions (log, info, statisctics, console, attach(
  - Stack
  - Image
  - Created
  - IP Address
  - Published Ports (mapping port with link to open address and port in browser)
- Images - List of images with information if the image is used. The used image cannot be deleted.
  - Build new image
  - Import
  - Export
  - Delete
  - Pull
- Networks - List of networks
  - New
  - Delete
- Volumes - List of volumes where information about driver, mount point, name
  - New
  - Delete
  - Browse (open browser)
    


