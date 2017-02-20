# apikana-java
The java side of [apikana](https://github.com/lbovet/apikana).

## Usage

### Create a new API project

Install apikana `npm install -g apikana`.
Run `apikana init`.

This starts an interactive wizard that lets you define the main aspects of the API project.

If you don't like `npm`, just take advantage of the provided parent pom and use this as a template:

````xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <parent>
        <groupId>org.swisspush.apikana</groupId>
        <artifactId>apikana-parent</artifactId>
        <version>0.1.16</version>
    </parent>

    <groupId>myorg.myproject</groupId>
    <artifactId>myapi</artifactId>
    <version>0.0.1-SNAPSHOT</version>
</project>
````

Create `src/rest/openapi/api.yaml`
````yaml
paths:
  /sample/users:
    get:
      operationId: getUser
      responses:
        200:
          description: ok
          schema:
            $ref: "#/definitions/User"
tsModels:
  - ../../model/ts/user.ts
````

And create `src/model/ts/user.ts`
````ts
export interface User {
    id: number
    firstName: string // The given name
    lastName: string // the family name @pattern [A-Z][a-z]*
    age?: number
}
````

### Create the API documentation

Just simply run `mvn install` and see the documentation at `http://localhost:8333`.

There is a complete [documentation](https://nidi3.github.io/apikana-java/site/generate-mojo.html) of the maven plugin.




