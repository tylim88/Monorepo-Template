<!-- markdownlint-disable MD010 -->
<!-- markdownlint-disable MD033 -->
<!-- markdownlint-disable MD041 -->

# Efficient Typescript Mororepo

<div align="left">
			<a
				href="https://github.com/tylim88/Efficient-Typescript-Mororepo/blob/main/LICENSE"
				target="_blank"
			>
				<img
					src="https://img.shields.io/github/license/tylim88/Efficient-Typescript-Mororepo"
					alt="License"
				/>
			</a>
		&nbsp;
			<a href="https://github.com/tylim88/Efficient-Typescript-Mororepo/actions" target="_blank">
				<img
					src="https://github.com/tylim88/Efficient-Typescript-Mororepo/workflows/CI/badge.svg"
					alt="github action"
				/>
			</a>
        &nbsp;
			<a href="https://github.com/tylim88/Efficient-Typescript-Mororepo/actions" target="_blank">
				<img
					src="https://github.com/tylim88/Efficient-Typescript-Mororepo/workflows/CodeQL/badge.svg"
					alt="github action"
				/>
			</a>
		&nbsp;
			<a href="https://github.com/tylim88/Efficient-Typescript-Mororepo/issues" target="_blank">
				<img
					alt="GitHub issues"
					src="https://img.shields.io/github/issues-raw/tylim88/Efficient-Typescript-Mororepo"
				></img>
			</a>
		&nbsp;
			<a href="https://snyk.io/test/github/tylim88/Efficient-Typescript-Mororepo" target="_blank">
				<img
					src="https://snyk.io/test/github/tylim88/Efficient-Typescript-Mororepo/badge.svg"
					alt="vulnerabilities"
				/>
			</a>
</div>
A minimal, optimal setup for modern web development projects using TypeScript.

(still in development, do not use)

## Technologies

This repo uses the following tech stack:

[Nx](https://nx.dev/) for managing and building monorepo applications  
[Docker](https://www.docker.com/) for containerizing the application and its dependencies  
[GitHub Actions](https://github.com/features/actions) for automating the build and deployment process  
[TypeScript](https://www.typescriptlang.org/) for static type checking and improved developer experience  
[Vite](https://vitejs.dev/) for fast development builds  
[Vitest](https://vitest.org/) for unit and integration testing  
[ESLint](https://eslint.org/) for enforcing a consistent code style  
[Prettier](https://prettier.io/) for formatting code consistently  
[Zod](https://zod.dev/) for validating and manipulating input data in a type-safe manner  
[tRPC](https://trpc.io/docs) for end-to-end typesafe APIs  
[Prisma](https://www.prisma.io/) for generating a type-safe database access layer  
[PostgreSQL](https://www.postgresql.org/) for storing data persistently  
[React](https://reactjs.org/) for building the user interface  
[Zustand](https://github.com/pmndrs/zustand) for simple React state management  
[Mantine](https://mantine.dev/) for providing a library of customizable and reusable UI components  
[Emotion](https://emotion.sh/docs/introduction) for styling components using CSS-in-JS  
[Cypress](https://www.cypress.io/) for end-to-end testing

## Getting Started

To get started with this repository, first clone and install the dependencies:

```bash
git clone https://github.com/tylim88/Efficient-Typescript-Mororepo.git
cd Efficient-Typescript-Mororepo
npm run setup
```

You can use the same script to re-setup the repository at any time.

Next, create an access token, follow the steps outlined in this [YouTube guide](https://youtu.be/w1-GiB74ddc?t=17). Instead of adding the access token to the `nx.json` file as shown in the video, refer to the [official guide](https://nx.dev/nx-cloud/account/access-tokens#using-) for instructions on how to place the access token in the `nx-cloud.env` file and configure it in your CI environment.

### Development

To run in development:

```bash
npm run dev
```

This will start the development server and open the application in your default browser.

### Build

To type check and build:

```bash
npm run build
```

### Testing

To run unit and integration tests:

```bash
npm test
```

To run end-to-end tests:

```bash
npm run e2e
```

### Linting

To run linting with fix and Prettier:

```bash
npm run lint
```

## Using Project Templates

There are five project templates, each with fine-tuned and simplified configurations:

1. `node-lib`: for general TypeScript/JavaScript libraries.
2. `jsdom-lib`: similar to `node-lib`, but specifically for code that manipulates the DOM.
3. `react-app`: for React applications.
4. `react-app-e2e`: for end-to-end testing of React applications.
5. `node-app`: for backend applications.

All templates include commands for linting and type checking.

The TypeScript and Vitest configurations for each template are extensively simplified without sacrificing functionality. In most cases, only the configuration files in root folder need to be modified.

Instruction on how to use templates:

### 1. Changing Project Names

Default projects names are unique enough that a search and replace function can be used to replace all instances of it. It may also be a good idea to keep copies of templates.

Note: the `react-app-e2e` project's `project.json` file also has instances of the `react-app` name, so be sure to update those as well when replacing the `react-app` name.

### 2. Updating the ESLint Configuration

If the template is a `react-app` or `react-app-e2e`, **update the existing** `files` field in the appropriate ESLint `override` to include the path to the new project.

For `react-app`:

```json
{
    "files": [
        "packages/my-react-app/**/*.{ts,tsx,js,jsx}",
        "packages/my-other-react-app/**/*.{ts,tsx,js,jsx}"
    ],
    "extends": ["plugin:@nrwl/nx/react"]
}
```

For `react-app-e2e`:

```json
{
    "files": [
        "packages/my-react-app-e2e/**/*.{ts,tsx,js,jsx}",
        "packages/my-other-react-app-e2e/**/*.{ts,tsx,js,jsx}"
    ],
    "extends": ["plugin:cypress/recommended"]
}
```

No action is required for the other templates.

## How Tools are Chosen

The selection of these technologies has been carefully considered, with an emphasis on enhancing the developer experience, ensuring type safety, and promoting code and configurations reusability. The use of this setup is expected to lead to software that is more maintainable and has a longer lifespan.

When choosing tools, the following four qualities are considered in this order of importance:

1. Type safety: Ensuring type safety is essential for code scaling. Types bring benefits such as autocompletion and intrinsic documentation, and can serve as a "single source of truth" by keeping everyone in sync. Type safety can also eliminate the need for unnecessary runtime type checks and corresponding tests, improving code efficiency and scalability.

2. Ease of use: There are an infinite number of technologies to learn, but everyone only has 24 hours per day. It is important to choose tools that are easy to learn, easy to discard, and easy to relearn in order to respect developers' time.

3. Functionality: Ease of use is prioritized over functionality because more powerful tools often have a higher learning cost than their simpler counterparts. For example, GraphQL is more powerful than REST, but may require more effort to learn and may not be necessary for many use cases. REST is often sufficient for most applications.

4. Performance: While performance is important, it should not be the top priority if you do not have a functional product. That being said, many of the tools mentioned in this list are known for their fast performance compared to alternatives.

## Core Technologies

Technologies such as Docker, ESLint, Prettier, and TypeScript are not discussed here, as they are considered standard choices at this point. The following technologies play long-term roles in development, including folder structuring (Nx), API design (Zod), and database interaction (Prisma):

1. Nx: At present, Nx is a superior choice to Turbo Repo. While Turbo Repo is written in a faster language, Nx is still faster and has more functionality, including a dependency graph and an integrated repository. Nx also has a larger and more mature community. The absence of an integrated repository is a significant drawback for Turbo Repo, while Nx's integrated repository makes it better for code reuse and maintenance.

2. Zod: There are many validation libraries available, but Zod stands out with its user-friendly API and type inference approach. It combines validation and API schema into one, making it the heart of your API design. Zod is a bit slow, however, and may not be suitable for parsing large amounts of data.

3. Prisma: Prisma is the ORM with the best type safety. (That being said, I am not a fan of the schema-first approach because it adds cognitive cost (the need to learn a schema language). I prefer a code-first approach, specifically a type-first approach (using types as schemas)).

4. tRPC: If you are using Zod, tRPC is a good choice for your server and client because it has the best type safety. Additionally, tRPC works best in a monorepo, which fits well with the structure of this project.

## Replaceable Techs

The following are tools that I highly recommend, but you are free to choose alternatives:

1. Vite: A fast development build tool that utilizes ESM to outperform Create React App (Webpack) in the development environment.

2. Vitest: Easier to configure and featuring a very fast watch mode compared to Jest, with an API similar to Jest for those familiar with the library.

3. GitHub Actions: A clean and easy-to-use UI for automating tasks, hosted by the same company as your code for faster performance.

4. React: While not the best UI library, React has excellent TypeScript support and a large community with plenty of resources.

5. Mantine: A well-designed React UI library with a modern API and great documentation, offering a wide range of components and useful hooks. Highly recommended.

6. Zustand: A simple and easy-to-use state management library.

7. Emotion: The technology behind Mantine, with a similar API to styled-components.

8. PostgreSQL: A reliable, free, and open-source SQL database, widely considered one of the best and working well with Prisma. It is important to use a database supported by Prisma to ensure type safety.

## Reusing Configuration

To reduce the number of configuration files and make maintenance easier, it is important to reuse configuration as much as possible. Here's how configuration is reused in this setup:

1. ESLint: There is only one `.eslintrc.js` file in the root directory, which applies to all files. The `override.files` field can be used to apply different rules to individual files or folders, so there is no need for additional configuration files. When generating a new project, simply add its path to `override.files`.

2. Prettier: There is only one `.prettierrc.js` file and one `.prettierignore` file in the root directory, which apply to all files.

3. Vite: Each project should have one `vite.config.ts` file that imports a preset from `vite.presets.ts` in the root directory.

4. There are fours TS config files in the root directory:

    - `tsconfig.base.json`: responsible for basic configuration and does not participate in any compilation. It is directly extended by React projects.

    - `tsconfig.json`: extends `tsconfig.base.json` and is responsible for files in the root directory (does not include subdirectories). It compiles but does not emit.

    - `tsconfig.cypress.json`: extends `tsconfig.base.json` and is used by Cypress projects.

    - `tsconfig.node.json`: extends `tsconfig.base.json` and is used by node projects.

### Common configs

Common configs are added as much as possible and as close to the root as possible, even if they are not applicable to all projects. For example, assuming the base TS configuration includes the following:

```json
{
    "compilerOptions": {
        "types": ["A", "B", "C"]
    }
}
```

Project `A` only requires type `A` and not `B` and `C`, but `B` and `C` are still added. This is done to reduce maintenance requirements. Without these additional configs, the TS config of Project `A` would need to be modified if type `A` is no longer needed or if type `B` is now required.

As long as it does not cause any issues, including uncommon configs in the base configuration can help improve maintenance and make our development process more efficient. If necessary, we can create additional configuration files to extend from the base configuration.

To summarize, the key to maintaining low maintenance configuration files is to refactor them as follows:

1. Keep the base files as close to the root directory as possible.
2. Include as many configs as possible in the base files.
3. Multiple sub-base files in the root directory may be required, each targeting a specific project type.

## Configuration Details

This section provides an in-depth look at the out-of-the-box configurations:

### 1. ESLint

1. Maintain a single ESLint config file at the root level, eliminating the need for project-level ESLint config files.
2. Utilize Prettier in conjunction with linting.
3. Ability to lint `.js`,`.jsx`,`.ts`,`.tsx`,`.json`,`.md`,`.yml` files.
4. All project templates run lint with the fix option enabled.
5. Ready for use with Husky and lint-staged(for pre-commit linting).
6. Remove unused imports during linting.
7. Ignore unused variables or arguments that are named with a leading `_`.
8. During pre-commit, Prettier is run a second time in addition to linting, as it covers a wider range of extensions.
9. Warn of `console.log` usage in the development environment, and throw errors for its use in pre-commit and CI. `console.info`, `console.warn`, and `console.error` do not trigger any warnings or errors. We allow `console.log` with a warning in development to accommodate common usage, but prevent its usage in pre-commit and CI to maintain a cleaner codebase.

### 2. Typescript Config

1. All project templates are ready for use with absolute paths.
2. Facilitate the import of CommonJS modules.
3. Allow for the import of CommonJS modules as the default export, even if there is no `exports.default`.
4. File names are case-sensitive.
5. Ensure all files are modules.
6. Ability to import and resolve JSON types.
7. Add the type `undefined` when using an index to access an array or object where the key type is `string`.
8. Prevent the assignment of `undefined` to types with optional modifiers, unless the optional type explicitly unions with `undefined`.

### 3. GitHub Actions

1. Caches node modules to improve build performance.
2. Ready for multi-OS and multi-node version strategy to ensure compatibility across different environments.
3. Build and Push Docker Image.
4. Ready for CodeQL.

## Final Thoughts

I hope this repository serves as a helpful starting point for your web development project and bring you the joy of development. The technologies listed above can help improve developer experience, ensure type safety, and promote code and configuration reusability. If you have any feedback, please don't hesitate to open an issue.
