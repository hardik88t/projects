# 🚀 Project Template

A standardized project template with comprehensive documentation and best practices for development projects. This template integrates with the [Project Manager](https://github.com/hardik88t/project-manager) webapp for feature and task tracking.

## 📋 Overview

This template provides a standardized structure for all development projects, including:
- **📝 Documentation Standards** (README, PLANNING, DEVLOG, GCP)
- **🔗 Project Manager Integration** (Feature tracking, task management)
- **🛠️ Development Workflow** (Git practices, commit standards)
- **☁️ Deployment Guidelines** (GCP setup and configuration)
- **🤖 AI Integration** (Database queries for project management)

## 🛠️ Template Features

### 📁 Standard Files
- **README.md** - Project overview, setup, and usage instructions
- **PLANNING.md** - Project planning, goals, and milestones
- **DEVLOG.md** - Development progress and technical decisions
- **GCP.md** - Google Cloud Platform setup and deployment guide
- **.env.example** - Environment variables template

### 🔗 Project Manager Integration
- **Database Connection** - Direct access to project manager SQLite database
- **Feature Tracking** - Query and update project features, bugs, improvements
- **Task Management** - Sync with centralized project management system
- **Progress Tracking** - Automated status updates and reporting

### 🤖 AI Assistant Integration
- **CLI Queries** - Standardized database queries for AI assistance
- **Project Context** - AI can access project features and status
- **Automated Updates** - AI can update task status and progress

## 📁 Project Structure

When you use this template, your project will have this structure:

```
your-project/
├── README.md              # Project overview and setup
├── PLANNING.md           # Project planning and goals
├── DEVLOG.md            # Development log and decisions
├── GCP.md               # Google Cloud Platform guide
├── .env.example         # Environment variables template
├── .gitignore           # Git ignore patterns
├── src/                 # Your project source code
├── docs/                # Additional documentation
└── scripts/             # Utility scripts
```

## 🚀 Quick Start

### 1. Use This Template
```bash
# Create new project from this template
gh repo create your-project-name --template hardik88t/projects --public
cd your-project-name
```

### 2. Set Up Project Manager Connection
```bash
# Copy environment template
cp .env.example .env

# Edit .env with your project manager database connection
# For local development:
PROJECT_MANAGER_DB="file:../project-manager/prisma/dev.db"
# For production:
PROJECT_MANAGER_DB="your-hosted-database-url"
```

### 3. Register Your Project
Add your project to the Project Manager webapp:
- Open Project Manager at http://localhost:3000
- Click "Add Project"
- Fill in project details
- Note the project ID for database queries

## � Project Manager Integration

### Database Connection
Your project can directly access the Project Manager database to get its features and tasks:

```bash
# Query your project's features (replace 'your-project-name' with actual name)
sqlite3 $PROJECT_MANAGER_DB "
  SELECT pi.name, pi.type, pi.status, pi.priority, pi.description
  FROM ProjectItem pi
  JOIN Project p ON pi.projectId = p.id
  WHERE p.name = 'your-project-name'
  ORDER BY pi.priority DESC, pi.createdAt ASC;
"

# Get high-priority TODO items for your project
sqlite3 $PROJECT_MANAGER_DB "
  SELECT pi.name, pi.description, pi.priority
  FROM ProjectItem pi
  JOIN Project p ON pi.projectId = p.id
  WHERE p.name = 'your-project-name'
  AND pi.priority IN ('HIGH', 'URGENT')
  AND pi.status = 'TODO';
"
```

### Update Task Status
When you complete features or fix bugs, update the status in Project Manager:

```bash
# Mark a feature as completed
sqlite3 $PROJECT_MANAGER_DB "
  UPDATE ProjectItem
  SET status='COMPLETED', updatedAt=datetime('now')
  WHERE name='Add dark mode toggle'
  AND projectId=(SELECT id FROM Project WHERE name='your-project-name');
"

# Mark a feature as in progress
sqlite3 $PROJECT_MANAGER_DB "
  UPDATE ProjectItem
  SET status='IN_PROGRESS', updatedAt=datetime('now')
  WHERE name='Implement user authentication'
  AND projectId=(SELECT id FROM Project WHERE name='your-project-name');
"
```

## 📚 Documentation Standards

Every project using this template includes:
- **README.md** - Project overview, setup instructions, and usage guide
- **PLANNING.md** - Project goals, milestones, and feature planning
- **DEVLOG.md** - Development progress, decisions, and technical notes
- **GCP.md** - Google Cloud Platform deployment and configuration guide
- **.env.example** - Environment variables template with Project Manager connection
- **Standardized Git workflow** with conventional commit messages

## 🛠️ Development Workflow

1. **Create Project** - Use this template to create new project repository
2. **Register in Project Manager** - Add project details and initial features
3. **Development** - Regular commits with conventional commit messages
4. **Feature Tracking** - Query Project Manager database for current tasks
5. **Progress Updates** - Update task status via CLI or Project Manager UI
6. **Documentation** - Maintain DEVLOG.md with development progress
7. **Deployment** - Follow GCP.md guide for cloud deployment

## 🤖 AI Assistant Integration

This template is designed to work seamlessly with AI assistants:

### For AI Assistants:
```bash
# Check what the user is working on
sqlite3 $PROJECT_MANAGER_DB "
  SELECT p.name, pi.name, pi.type, pi.priority, pi.status, pi.description
  FROM ProjectItem pi
  JOIN Project p ON pi.projectId = p.id
  WHERE pi.status IN ('TODO', 'IN_PROGRESS')
  AND pi.priority IN ('HIGH', 'URGENT')
  ORDER BY pi.priority DESC;
"

# Update progress when completing tasks
sqlite3 $PROJECT_MANAGER_DB "
  UPDATE ProjectItem
  SET status='COMPLETED', updatedAt=datetime('now')
  WHERE id='[item-id]';
"
```

## 📋 Template Files

This repository includes these template files:

- **README.md** - This file, explains the template system
- **PLANNING.md** - Template for project planning and goals
- **DEVLOG.md** - Template for development logging
- **GCP.md** - Google Cloud Platform deployment guide
- **.env.example** - Environment variables template

When you create a new project, customize these files for your specific project.

## � Related Repositories

- **Project Manager**: [hardik88t/project-manager](https://github.com/hardik88t/project-manager) - Central webapp for managing all projects
- **Template Repository**: [hardik88t/projects](https://github.com/hardik88t/projects) - This template repository

## 📄 License

This template is open source and available under the [MIT License](LICENSE).

## 🔗 Links

- **Planning Template**: [PLANNING.md](./PLANNING.md)
- **Development Log Template**: [DEVLOG.md](./DEVLOG.md)
- **GCP Guide**: [GCP.md](./GCP.md)
- **GitHub Profile**: [@hardik88t](https://github.com/hardik88t)

---

⭐ **Star this repository** if you find this template useful!

🚀 **Use this template** to standardize your development projects!
