
## Project setup

```bash
$ npm install
```

## Compile and run the project

```bash
# development
$ npm run start

# watch mode
$ npm run start:dev

# production mode
$ npm run start:prod
```

## Run tests

```bash
# unit tests
$ npm run test

# e2e tests
$ npm run test:e2e

# test coverage
$ npm run test:cov
```

### Lint and autofix with eslint
 npm run lint

### Format with prettier
 npm run format

#### Understanding Dependency Injection with Architecture

- In a traditional, non-DI setup, components or classes are directly responsible for creating instances of their dependencies. For example, if a UserService depends on a DatabaseService, the UserService itself would create or locate the DatabaseService, which tightly couples them. DI reverses this by externalizing the responsibility of dependency creation to a container or framework, allowing dependencies to be injected into components as needed.

#### How Dependency Injection Works in Layers
Let’s look at how DI works within a multi-layer architecture, which is common in both backend (NestJS) and frontend (Angular) applications:

- DI Container/Injector: At the core, both frameworks have an injector that manages dependencies. When the application starts, the injector creates instances of classes based on configuration, and these instances are stored and managed.
- Dependency Registration: Services are registered in modules with a decorator like @Injectable() (in both NestJS and Angular). This marks them as providers so that they’re available for injection in other parts of the application.
- Dependency Resolution: When a class (e.g., a controller in NestJS or a component in Angular) declares a dependency in its constructor, the DI container searches for a registered instance of the requested dependency.
- Injection: Once the DI container finds the dependency, it injects it directly into the requesting class’s constructor.

#### Example Architecture with Dependency Injection in NestJS

In a NestJS application with layered architecture, let's say we have these layers:

- Controller Layer: Manages HTTP requests and responses.
- Service Layer: Contains the business logic and processes data.
- Repository Layer: Manages data storage and retrieval.

- Repository Layer: Define a UserRepository class for database interactions, decorated with @Injectable so that it can be injected.
- Service Layer: Define a UserService that depends on UserRepository. The UserService does not need to know how UserRepository is instantiated—it only declares a dependency on it.
- Controller Layer: The controller layer (e.g., UserController) can then inject UserService and use it for handling HTTP requests.
- Module Registration: In NestJS, these classes are registered in a module, which tells the DI container about their availability.

- The Controller depends on UserService, which in turn depends on UserRepository.



