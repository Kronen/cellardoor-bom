# CellarDoor BOM

Parent POM providing dependency and plugin management for CellarDoor projects.

## Usage

### 1. Add as Parent POM

Include this BOM as the parent in your project's `pom.xml`:

```xml
<parent>
    <groupId>com.github.kronen</groupId>
    <artifactId>cellardoor-bom</artifactId>
    <version>0.12.0</version>
    <relativePath/>
</parent>
```

### 2. Required Configuration Files

Your project must include the following files in the root directory:

- `checkstyle.xml` (mandatory)
- `checkstyle-suppressions.xml` (optional)

### 3. OpenAPI Configuration

To generate API interfaces, your project must include an OpenAPI specification file at:
```
${project.basedir}/src/main/resources/api/openapi.yaml
```

The OpenAPI plugins will:
- Skip execution if this file is not present
- When present:
    1. Bundle the OpenAPI specification using Redocly
    2. Generate Spring interfaces and DTOs based on the specification

Example module structure:
```
your-project/
├── api-module/
│   └── src/main/resources/
│       └── api/
│           └── openapi.yaml    # Place your OpenAPI spec here
└── pom.xml
```

### 3. SCM Configuration

Add your project's SCM information. Example:

```xml
<scm>
    <connection>scm:git:https://github.com/your-username/your-project.git</connection>
    <developerConnection>scm:git:https://github.com/your-username/your-project.git</developerConnection>
    <url>https://github.com/your-username/your-project</url>
    <tag>HEAD</tag>
</scm>
```

## Features

- Java 21 support
- Spring Boot 3.4.2 compatibility
- Managed dependencies:
  - Lombok
  - MapStruct
  - Commons Lang
  - Swagger Annotations
  - Testing frameworks

## Included Plugins

- Spring Boot Maven Plugin
- Git Flow Maven Plugin
- Git Commit ID Maven Plugin
- Maven Compiler Plugin
- Maven Enforcer Plugin
- Checkstyle Plugin
- Spotless Plugin
- OpenAPI Generator Plugin

## Requirements

- Maven 3.9.9+
- Java 21
- Git

## License

GNU General Public License v3.0

