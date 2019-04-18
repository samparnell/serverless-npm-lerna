# serverless-npm-lerna
Demo Repo for a setup using Lerna to manage NPM packages and Lambda Functions

## Structure
This repo has the following structure. It combines all backend Serverless
functions and packages into a single structure. Lerna is leveraged to manage
shared dependencies across the entire codebase.

```
├── packages
│   ├── package-group
│   │   ├── package-a
│   │   └── package-b
│   └── package-c
├── services
│   ├── service-group-a
│   │   ├── service-a-1
│   │   └── service-a-2
│   ├── service-group-b
│   │   ├── service-b-1
│   │   └── service-b-2
│   └── service-c
├── package.json - Shared dependencies and scripts
├── lerna.json - Lerna configuration
├── eslint.config.js - Shared ESLint configuration
└── jest.config.js - Shared Jest configuration
```

## Best Practices
Group your services and packages into logic groupings. This can make it easier to
say deploy/publish api functions as a group.

Put lint rules at the root to maintain consistency across the board. You are able
to run a lint fix from the root for the whole project or filtered to a section.

Install dependencies that are required to run as scripts in the context of a package
within the package. For example, if running Jest include that within the package
devDependencies. If something is run purely at the root level (eg eslint) then just
include those in the root package.json.
An alternative to this is to symlink the node_modules/.bin/files to the root
but requires extra steps to set up and maintain.
