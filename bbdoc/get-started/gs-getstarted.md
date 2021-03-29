# Get Started

User documentation for the platform is accessible at

## Accessing the platform

The platform requires a provisioned tenant in the Illumina account management system with access to the Illumina Analytics Platform \(IAP\) application. Once a tenant has been provisioned, a tenant administrator will be assigned. The tenant administrator has permission to add users, create workgroups, and manage account access. Each tenant is assigned a domain name used to login to the platform. The domain name is used in the login URL to navigate to the appropriate login page in a web browser. The login URL is `https://<domain>.login.illumina.com`, where `<domain>` is substituted with the domain name assigned to the tenant.

New user accounts can be created for a tenant by navigating to the domain login URL and following the links on the page to setup a new account with a valid email address. Once the account has been added to the domain, the tenant administrator may assign registered users to workgroups with permission to use the IAP application. Registered users may also be made workgroup administrators by tenant administrators or existing workgroup administrators. Without being added to a workgroup, registered users will be limited to read-only operations on the platform. Once added to a workgroup, the full set of permissions is granted.

For more details on identity and access management, see the

### Generate an API Key

For long-lived credentials to the API, an API Key can be generated from the account console and used with the API and command-line interface. Each user is limited to 10 API Keys.

1. Login through the domain URL
2. Select your user name in the top-right of the view to open the drop-down and select "Manage API Keys".
3. Use the "+" button to generate new API Keys or the action buttons to modify, delete, or change the roles associated with any existing API Keys.

> After generating an API key, save the key somewhere secure to be referenced when using the command-line interface or APIs.

### Access via the Web User Interface

The web application provides a visual user interface for navigating resources in the platform, managing projects, and extended features beyond the API. To access the web application, navigate to your domain login URL through a web browser and login to the account console. Once logged in, select the IAP application from the list of available applications to be directed to the IAP web application console.

### Access via the Command-line Interface

The command-line interface offers a developer-oriented experience for interacting with the APIs to manage resources and launch analysis workflows. Find instructions for using the command-line interface including download links for your operating system in the

### Access via the API

The HTTP-based application programming interfaces \(APIs\) are listed in the section of the documentation. The reference documentation provides the ability to call APIs from the browser page and shows detailed information about the API schemas. HTTP client tooling such as Postman or cURL can be used to make direct calls to the API outside of the browser.

> When accessing the API using the API Reference page or through REST client tools, the `Authorization` header must be provided with the value set to `Bearer <token>` where `<token>` is replaced with a valid JSON Web Token \(JWT\). For generating a JWT, see.

## Projects

Projects provide an access-controlled workspace for organizing and sharing resources created in the platform. Data can be added to a project and shared among workgroups, a collection of users, within the owning account.

The platform console GUI provides the interface for adding and removing shares to workgroups. Workgroups can be shared to by users with access to the project, only if the project owner has membership in the target workgroup. A share is made with a role assigned to the target workgroup within the project context. Each role has a set of permissions which will be granted to members of the workgroup within the shared project.

| Role | Description |
| :--- | :--- |
| Viewer | Read-only access \(includes data download\) |
| Contributor | Read/write access |
| Administrator | Read/write access, create shares |

The Data section within a project shows files and folders in specific locations in the underlying storage service. Upon creating a project, a "home" GDS volume is created with a name based on the project name with the following modifications:

* Spaces removed
* All lowercase

