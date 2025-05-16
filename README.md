# Tasks App

A simple task management application built with Vue 3, TypeScript, and Vite. This app demonstrates component-based architecture, state management, and modern frontend tooling.

**This app is based on a YouTube video by the channel called Syntax.**

## Features
- Add, filter, and list tasks
- Component-based structure (`TaskForm`, `TaskList`, `FilterButton`)
- TypeScript support
- Fast development with Vite

## Project Structure
```
├── public/                # Static assets
├── src/
│   ├── App.vue            # Main app component
│   ├── main.ts            # App entry point
│   ├── style.css          # Global styles
│   ├── types.ts           # TypeScript types
│   ├── components/
│   │   ├── FilterButton.vue
│   │   ├── TaskForm.vue
│   │   └── TaskList.vue
│   └── assets/            # App assets
├── index.html             # HTML entry point
├── package.json           # Project metadata and scripts
├── tsconfig*.json         # TypeScript configuration
├── vite.config.ts         # Vite configuration
└── README.md              # Project documentation
```

## Getting Started

### Prerequisites
- Node.js (v16+ recommended)
- pnpm (or npm/yarn)

### Install dependencies
```bash
pnpm install
```

### Start development server
```bash
pnpm dev
```

### Build for production
```bash
pnpm build
```

### Preview production build
```bash
pnpm preview
```

## Learn More
- [Vue 3 Documentation](https://vuejs.org/)
- [Vite Documentation](https://vitejs.dev/)
- [TypeScript Documentation](https://www.typescriptlang.org/)

## License
MIT
