## Next.js Naming Conventions



| Type                | Naming Convention            | Example                          |
|---------------------|------------------------------|----------------------------------|
| Page                | lowercase-with-dashes        | `index.js`, `about.js`           |
| Dynamic Route       | inside-square-brackets       | `[id].js`, `[slug].js`           |
| API Route           | descriptive-lowercase        | `users.js`, `[id].js`            |
| Component           | PascalCase                   | `Header.js`, `LoginForm.js`      |
| Folder              | lowercase                    | `components`, `pages`            |
| Utility Function    | camelCase                    | `formatDate.js`, `apiUtils.js`   |
| Global Styles       | global.css                   | `global.css`                     |
| Configuration File  | descriptive-lowercase       `| `next.config.js`, `babel.config.js` |
| Package.json Script | lowercase-with-dashes        | `"start": "next dev"`, `"build": "next build"` |
| Public Asset        | lowercase-with-dashes        | `logo.png`, `favicon.ico`        |

   


1. **Page Naming**:
   - Pages in Next.js are typically named after the route they represent.
   - Use lowercase letters and dashes to separate words.
   - Example: `index.js`, `about.js`, `user-profile.js`.

2. **Dynamic Routes**:
   - Dynamic routes are enclosed in square brackets `[]`.
   - Use meaningful names inside the brackets.
   - Example: `[id].js`, `[slug].js`, `[username].js`.

3. **API Routes**:
   - API routes should be placed inside the `/pages/api` directory.
   - Use descriptive names for API routes.
   - Example: `/pages/api/users.js`, `/pages/api/posts/[id].js`.

4. **Component Naming**:
   - Component names should be descriptive and use PascalCase.
   - Use meaningful names that reflect the purpose of the component.
   - Example: `Header.js`, `UserProfileCard.js`, `LoginForm.js`.

5. **Folder Naming**:
   - Folder names should be lowercase and descriptive.
   - Use plural nouns for directories containing multiple files of the same type.
   - Example: `components`, `pages`, `styles`, `utils`.

6. **Utility Functions**:
   - Utility functions should be named descriptively and use camelCase.
   - Prefix utility function names with a relevant term if necessary.
   - Example: `formatDate.js`, `apiUtils.js`, `stringHelpers.js`.

7. **Global Styles**:
   - Global CSS files should be named `global.css`.
   - Use lowercase letters and dashes to separate words if necessary.
   - Example: `global.css`.

8. **Configuration Files**:
   - Configuration files should be named after their purpose.
   - Use `next.config.js` for Next.js configuration.
   - Example: `next.config.js`, `babel.config.js`, `eslint.config.js`.

9. **Package.json Scripts**:
   - Scripts in `package.json` should be named descriptively.
   - Use lowercase letters and dashes to separate words.
   - Example: `"start": "next dev"`, `"build": "next build"`.

10. **Public Assets**:
    - Public asset filenames should be descriptive and lowercase.
    - Use dashes to separate words if necessary.
    - Example: `logo.png`, `favicon.ico`, `background-image.jpg`.
