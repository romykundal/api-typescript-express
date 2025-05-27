# romykundal.dev api-typescript-express
A clean and minimal starter project for Node.js, Express.js, and TypeScript, ideal for small to medium-sized applications.

Designed with simplicity and scalability in mind, this boilerplate offers a solid foundation for personal or MVP projects.

While larger applications may require additional folder structuring, this template is easily extensible and flexible enough to evolve with your project’s needs.

## Features
Most of the essential features are pre-configured to streamline setup, letting you focus on development rather than boilerplate. Additional packages are also included to accelerate your project from the get-go.

Full TypeScript support for type-safe development

Jest pre-configured for seamless testing with TypeScript

Async/await-ready with built-in error handling middleware

Database/ORM agnostic, allowing flexible integration

Path aliases for cleaner and maintainable imports

Nodemon for automatic server restarts on file changes

Optimized production build with dedicated scripts (no ts-node in prod)

Pre-configured security middlewares for safer applications

Environment variables autoloaded, ready for multi-environment configs

# Setup

## Environment Variables

1. Copy ```.env.example```, and rename to ```.env```
2. Configure newly copied ```.env``` file 

## Development
> This project was setup using Node.js v18.5. Please use specified version for best experience.

1. Use this project as a template
2. Install dependencies with ```npm install```
3. Start developoment server with ```npm run dev```

## Production
Production build is compiled first into JavaScript, built on the ```./dist``` folder, and can be ran after compilation.

1. Run ```npm run build```
2. Run ```npm run start```

# Project
Every development files are located within the ```./src``` folder. 

```
├── app.ts
├── config
│   └── db.ts
├── controllers
│   └── user-controller.ts
├── middleware
│   ├── async-middleware.ts
│   ├── auth-middleware.ts
│   └── error-middleware.ts
├── routes
│   └── user-route.ts
├── __tests__
│   └── example.test.ts
├── types
│   ├── enums
│   │   └── enums.common.ts
│   ├── interfaces
│   │   └── interfaces.common.ts
│   └── types
│   │   └──  types.common.ts
│   └── index.d.ts
└── utils
    ├── ApiError.ts
    └── ApiSucess.ts
```

## Important helper functions

### asyncHandler
Passing middleware into the asyncHandler will allow the server to automatically catch any internal server errors, or manually thrown errors from the server. 
```js
// ? asyncHandler should be used for every request for easy async handling
export const getUsers = asyncHandler(
  async (req: Request, res: Response, next: NextFunction) => {
    // Example user, get from database
    const user = [{ name: "romy kundal" }, { name: "romy Gharota" }];

    // Return json with success message
    res.status(200).json(new ApiSuccess<User[]>(user, "Success!"));
  },
);
```

## ApiError & ApiSucccess
Using ApiError or ApiSuccess allows for consistent responses across all routes; please use this instead of passing your own data structure. 

### ApiError
```js
 throw new ApiError({}, 500, "Handled by asyncHandler")
```

### ApiSuccess
```js
 res.status(200).json(new ApiSuccess<User[]>(user, "Success!"));
```

## Adding extra path aliases
If you add extra folders to this template and would like to use them with aliases, then go through following:

1. Go into ```tsconfig.json```
2. Add extra paths inside of ```{ paths: ... }``` (for tsconfig-paths)
3. Go into ```package.json```
4. Add extra paths inside of ```{_moduleAliases: ... }``` (for production build)

## 🧑‍💻 Developer Info
- **Author**: [Rohit Kumar](https://www.romykundal.dev/)  
- **GitHub**: [@romykundal](https://github.com/romykundal)  
- **Email**: romykundal@gmail.com
