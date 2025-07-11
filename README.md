# 🚀 Projects Collection

A comprehensive collection of 200+ modern project templates across different tech stacks and use cases. Each template is production-ready with comprehensive documentation and best practices.

**🎯 NEW: This repository now includes a built-in Project Management Webapp** - A Next.js + TypeScript + shadcn/ui application to manage and track all projects in this collection.

## 📋 Overview

This repository serves as the central hub for project templates that cover:
- **Websites & Web Applications** (Portfolio, Business, E-commerce, Dashboards)
- **CLI Tools & Utilities** (File processors, Dev tools, System utilities)
- **APIs & Backend Services** (REST, GraphQL, Microservices)
- **Mobile Applications** (React Native, Flutter, PWAs)
- **Desktop Applications** (Electron, Tauri, Native)
- **Browser & VS Code Extensions**
- **AI/ML Projects** (OpenAI integrations, Local models, AI tools)
- **DevOps & Infrastructure** (Docker, CI/CD, Monitoring)
- **Popular App Clones** (Netflix, Spotify, Slack, etc.)

## 🛠️ Tech Stack Coverage

### Frontend
- **React** (Vite, Next.js) with **ShadCN/UI** ⭐
- **Vue.js** (Nuxt.js) with Tailwind CSS
- **Angular** with Material Design
- **Svelte/SvelteKit** with modern styling
- **Vanilla JavaScript** with Web Components
- **HTMX** for server-side rendered apps

### Backend
- **Node.js** (Express, Fastify, NestJS)
- **Python** (Django, FastAPI, Flask)
- **Go** (Gin, Echo, Fiber)
- **Rust** (Axum, Actix-web)
- **Java** (Spring Boot)
- **Ruby** (Rails)

### Databases & Services
- **PostgreSQL**, **MongoDB**, **SQLite**
- **Supabase**, **Firebase**
- **Redis** for caching
- **Prisma** ORM

### Deployment & Infrastructure
- **Vercel**, **Netlify**, **Railway**
- **Docker** & **Docker Compose**
- **GitHub Actions** CI/CD
- **Custom server deployment**

## 📁 Repository Structure

Each project is maintained as a separate GitHub repository and linked here as git submodules:

```
projects/
├── project-manager/   # 🆕 Next.js webapp to manage all projects
├── websites/          # Portfolio, business, e-commerce sites
├── web-apps/          # Dashboards, blogs, social media apps
├── cli-tools/         # Command-line utilities and tools
├── apis/              # REST APIs, GraphQL, microservices
├── mobile/            # React Native, Flutter, PWA apps
├── desktop/           # Electron, Tauri desktop applications
├── browser-extensions/ # Chrome, Firefox extensions
├── vscode-extensions/ # VS Code development tools
├── ai-projects/       # AI/ML integrations and tools
├── devops/           # Docker, CI/CD, monitoring templates
└── clones/           # Popular app clones and demos
```

## 🎯 Featured Projects

### 🌟 ShadCN/UI Showcase
- **portfolio-react-shadcn** - Modern portfolio with React + ShadCN/UI
- **dashboard-react-shadcn** - Admin dashboard with charts and analytics
- **task-manager-react-shadcn** - Task management with drag & drop
- **ecommerce-nextjs-shadcn** - E-commerce with Stripe integration

### 🤖 AI-Powered Applications
- **chatgpt-clone-react-openai** - ChatGPT interface with OpenAI API
- **image-generator-nextjs-dalle** - AI image generation with DALL-E
- **code-assistant-vscode-openai** - VS Code extension with AI code help
- **document-chat-python-ollama** - Chat with documents using local AI

### 🔥 Popular Clones
- **netflix-clone-react-nodejs** - Netflix-style streaming platform
- **spotify-clone-vue-express** - Music streaming application
- **slack-clone-react-socketio** - Team communication platform
- **notion-clone-nextjs-supabase** - Note-taking and productivity app

## 🚀 Quick Start

### Clone with Submodules
```bash
# Clone the main repository with all submodules
git clone --recursive https://github.com/hardik88t/projects.git

# Or clone and then initialize submodules
git clone https://github.com/hardik88t/projects.git
cd projects
git submodule update --init --recursive
```

### 🆕 Project Management Webapp
```bash
# Navigate to the project manager
cd project-manager

# Install dependencies
npm install

# Set up the database
npx prisma migrate dev

# Start the development server
npm run dev
```

### Browse Individual Projects
Each project has its own repository with detailed setup instructions:

1. Navigate to the project category folder
2. Enter the specific project directory
3. Follow the README.md instructions for setup
4. Check DEVLOG.md for development insights

## 📚 Documentation Standards

Every project includes:
- **README.md** - Setup, usage, and deployment guide
- **DEVLOG.md** - Development progress and technical decisions
- **GOALS.md** - Project objectives (for complex projects)
- **Environment setup** with `.env.example`
- **Docker configuration** where applicable
- **CI/CD workflows** for automated testing and deployment

## 🛠️ Development Workflow

1. **Project Proposal** - Each new project is proposed with tech stack and features
2. **Repository Creation** - Individual GitHub repo created with `gh` CLI
3. **Development** - Regular commits with conventional commit messages
4. **Documentation** - Comprehensive docs written throughout development
5. **Testing & Deployment** - CI/CD setup and deployment configuration
6. **Submodule Integration** - Project linked to main projects repository

## 🎯 Current Progress

- **Phase 1**: Foundation Projects (20 projects) - 🚧 In Progress
- **Phase 2**: Diversification (40 projects) - 📋 Planned
- **Phase 3**: Advanced & Specialized (60 projects) - 📋 Planned
- **Phase 4**: Completion & Polish (80+ projects) - 📋 Planned

**Target**: 200+ comprehensive project templates

## 🤝 Contributing

While this is primarily a personal template collection, suggestions and feedback are welcome:

1. **Issues** - Report bugs or suggest improvements
2. **Discussions** - Share ideas for new project templates
3. **Pull Requests** - Improvements to documentation or fixes

## 📄 License

Each project may have its own license. Check individual project repositories for specific licensing information.

## 🔗 Links

- **Planning Document**: [PLANNING.md](./PLANNING.md)
- **Development Log**: [DEVLOG.md](./DEVLOG.md)
- **GitHub Profile**: [@hardik88t](https://github.com/hardik88t)

---

⭐ **Star this repository** if you find these templates useful!

🚀 **Follow the journey** as we build 200+ modern project templates!
