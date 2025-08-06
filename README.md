```
███████╗██╗      █████╗ ███████╗██╗  ██╗██████╗  █████╗  ██████╗██╗  ██╗███████╗██████╗ 
██╔════╝██║     ██╔══██╗██╔════╝██║  ██║██╔══██╗██╔══██╗██╔════╝██║ ██╔╝██╔════╝██╔══██╗
█████╗  ██║     ███████║███████╗███████║██████╔╝███████║██║     █████╔╝ █████╗  ██████╔╝
██╔══╝  ██║     ██╔══██║╚════██║██╔══██║██╔══██╗██╔══██║██║     ██╔═██╗ ██╔══╝  ██╔══██╗
██║     ███████╗██║  ██║███████║██║  ██║██████╔╝██║  ██║╚██████╗██║  ██╗███████╗██║  ██║
╚═╝     ╚══════╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝╚═════╝ ╚═╝  ╚═╝ ╚═════╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝
                                                                                          
         ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░
       ░░▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒░░
     ░░▒▒▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▒▒░░
   ░░▒▒▓▓██████████████████████████████████████████████████████████████████▓▓▒▒░░
 ░░▒▒▓▓████  M E M O R I E S   F L O A T I N G   B A C K   I N   T I M E  ████▓▓▒▒░░
   ░░▒▒▓▓██████████████████████████████████████████████████████████████████▓▓▒▒░░
     ░░▒▒▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▒▒░░
       ░░▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒▒░░
         ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░
```

> **Claude Code state management with session continuity and AI personas**

Flashbacker provides **session continuity** for Claude Code through intelligent state management and specialized AI personas accessed via `/fb:` slash commands.

**Current Status: v2.2.6** - 🚧 **ALPHA** - Critical framework coexistence fixes with dynamic template scanning. Fixed catastrophic init system bug that destroyed other Claude frameworks. Bulletproof multi-framework coexistence.

## 🚀 Quick Start

### Prerequisites

- **Node.js**: 18.x, 20.x, or 22.x LTS (recommended: 22.x)
- **npm**: 9.x or later

#### Quick Prerequisites Installation
```bash
# Option 1: Use our automated installer script
npm run setup:prereqs

# Option 2: Manual nvm installation (recommended)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
nvm install 22
nvm use 22

# Option 3: Download from https://nodejs.org/ (LTS version)
```

### Quick Installation
```bash
# Clone and build
git clone https://github.com/agentsea/flashbacker.git
cd flashbacker
npm install && npm run build && npm link

# Initialize with MCP servers (RECOMMENDED)
cd /path/to/your/project
flashback init --mcp              # Includes context7, playwright, sequential-thinking
```

> 📖 **[Complete Installation Guide →](docs/user-guide/INSTALLATION.md)**  
> Comprehensive setup instructions, troubleshooting, and advanced options

## 🎯 How You Actually Use Flashbacker

After installation, you use Flashbacker through **slash commands in Claude Code**:

### Primary Commands (What You'll Use Daily)
```bash
# Persona Analysis (Current Conversation)
/fb:persona architect "review our API design"     # Get specialized AI analysis
/fb:persona security "analyze authentication"     # Security expert analysis  

# Agent Analysis (Dedicated Subagents with Project Context)
@agent-architect "analyze our microservices architecture"
@agent-security "comprehensive security audit of auth system"
@agent-performance "deep performance analysis with recommendations"
@agent-qa "create comprehensive testing strategy"

# Session Management
/fb:working-plan                                  # Update development priorities
/fb:save-session                                  # Capture session insights
/fb:how                                           # Plan implementation before coding
/fb:how "specific topic"                              # Plan implementation for specific topic only
/fb:remember key insight or decision              # Save important info to memory

# Code Quality Analysis
/fb:debt-hunter                                   # Hunt technical debt and code quality issues
/fb:hallucination-hunter                          # Hunt AI-generated code that doesn't work
```

### What Happens Behind the Scenes
When you run `/fb:persona architect "review API"`:
1. **CLI gathers context**: Loads project memory, working plan, conversation history
2. **Template processing**: Applies architect persona template with your request
3. **Formatted output**: Provides structured prompt for Claude's Task tool
4. **You get**: Specialized architectural analysis with full project context

## ✨ Core Features

### 🧠 **Session Continuity System**
- **SessionStart Hook**: Automatically loads project memory + working plan after compaction
- **Memory Injection**: REMEMBER.md prevents repeated corrections across sessions  
- **Working Plan Intelligence**: AI analyzes conversations to update development plans

### 🎭 **Dual-Layer AI System**

**Layer 1: Personas (Current Conversation)**
- `/fb:persona architect "analyze API design"` - Direct template application
- All 12 personas available for immediate analysis in current conversation

**Layer 2: Agents (Dedicated Subagents)** 
- `@agent-architect "analyze API design"` - Spawns dedicated subagent with full project context
- Agents automatically gather context via `flashback agent --context`
- Project-aware analysis with REMEMBER.md, WORKING_PLAN.md, conversation history

**Available Specialists:**
- **architect**: Systems architecture, scalability, long-term design
- **security**: Threat modeling, vulnerability assessment
- **backend**: APIs, reliability, data integrity
- **frontend**: UX, accessibility, performance
- **analyzer**: Root cause analysis, investigation
- **mentor**: Knowledge transfer, documentation
- **refactorer**: Code quality, technical debt
- **performance**: Optimization, bottlenecks
- **qa**: Testing, quality assurance
- **devops**: Infrastructure, deployment
- **product**: User needs, business strategy
- **code-critic**: Code quality enforcement

### 🔄 **State Management**
- **Dynamic Template Scanning**: Zero hardcoded paths, everything from bundled templates
- **Memory System**: Persistent project knowledge across sessions
- **Working Plan**: AI-powered development priority tracking

### 🔌 **MCP Server Integration**
- **context7**: Up-to-date documentation and library context for any framework
- **playwright**: Browser automation, testing, and web interaction capabilities  
- **sequential-thinking**: Advanced multi-step reasoning and problem-solving chains

## 🎯 Slash Commands You'll Use

### Persona Analysis (Current Conversation)
```bash
/fb:persona architect "should we refactor the database layer?"
/fb:persona security "review authentication in src/auth/"
/fb:persona performance "optimize our query performance"
/fb:persona qa "what edge cases should we test?"
```

### Agent Analysis (Dedicated Subagents)
```bash
@agent-architect "analyze our microservices architecture"
@agent-security "comprehensive security audit of auth system"
@agent-performance "deep performance analysis with recommendations"
@agent-qa "create comprehensive testing strategy"
```

### Session Management
```bash
/fb:working-plan          # Update development plan with AI analysis
/fb:save-session         # Capture session insights before compaction
/fb:session-start        # Load project context (runs automatically via hook)
/fb:how                  # Implementation planning prompt (plan before coding)
/fb:how "specific topic"         # Focused planning for specific topic only
/fb:remember important insight here  # Add key information to project memory
/fb:persona-list         # Show all available AI personas with descriptions
/fb:agents-list          # Show all available Claude Code agents with descriptions
/fb:discuss architect,security "topic"  # Multi-agent discussion coordination
```

### Multi-Language Code Quality Analysis
```bash
/fb:debt-hunter                      # Hunt technical debt across 6 programming languages
/fb:debt-hunter duplicates           # Focus on duplicate function detection
/fb:debt-hunter comprehensive        # Full analysis (debt + duplicates)
/fb:hallucination-hunter             # Hunt AI-generated code that doesn't actually work

# Automatically detects and analyzes:
# - JavaScript/TypeScript: console.log(), debugger;, empty functions
# - Python: print(), pdb.set_trace(), NotImplementedError
# - Go: fmt.Println(), panic(), runtime.Breakpoint()
# - Java: System.out.println(), UnsupportedOperationException
# - Rust: println!(), panic!(), unimplemented!()
# - Universal patterns: TODO comments, generic names, similar functions
```

### Memory Management
```bash
# Add key information to project memory:
/fb:remember important architectural decision about database design

# View current project memory:
flashback memory --show
```

## 🏗️ How It Works

### 1. Installation & Setup
- Run `flashback init --mcp` once per project (recommended)
- Creates `.claude/flashback/` directory structure  
- Installs SessionStart hook for automatic context loading
- Configures powerful MCP servers for enhanced capabilities

### 2. Daily Usage
- Use `/fb:persona <name> "request"` for specialized analysis
- Use `/fb:working-plan` to keep development priorities current  
- Use `/fb:save-session` before major context compactions
- Memory automatically loads via SessionStart hook

### 3. Behind the Scenes
- **CLI**: Gathers project context, loads templates, formats prompts
- **Claude**: Executes Task tool with specialized persona prompts
- **Hybrid Pattern**: Computer handles data, AI handles intelligence

## 🔧 Advanced Features

### Discussion System
```bash
# CLI command for multi-persona debates:
flashback discuss "Should we use microservices?" --personas architect,devops,security
```

### Diagnostics (When Things Go Wrong)
```bash
flashback doctor          # Check system health
flashback status          # Verify installation
flashback init --refresh  # Update templates
flashback init --mcp      # Add MCP servers to existing setup
```

## 🏗️ Architecture

### Template-Driven System
- **Dynamic Directory Scanning**: Reads bundled templates at runtime
- **Zero Hardcoded Paths**: All structure derived from template bundle
- **Variable Replacement**: {{PROJECT_NAME}}, {{VERSION}}, {{TIMESTAMP}}
- **Version Sync**: Automatically uses package.json version

### Hybrid AI+Computer Operations
- **CLI**: Handles programmatic operations (file management, data extraction)
- **AI**: Handles intelligence operations (analysis, planning, decisions)
- **Clear Separation**: Computer does deterministic work, AI does creative work

## 🔧 Requirements

- **Node.js 18.x-22.x LTS**: Required for tree-sitter native modules and modern features  
- **npm 9.x+**: Required for lockfile version 3 support
- **Claude Code**: Latest version for hook system compatibility

**⚠️ Note**: Versions outside the Node.js 18-22 range may cause native module compilation errors.

## 🔒 Security

Flashbacker automatically excludes `.claude/` from git commits to protect sensitive data.

## 📄 License

MIT License

---

**v2.2.6 Status**: 🚧 **ALPHA** - Critical framework coexistence fixes with dynamic template scanning + **NEW: MCP Server Integration**. Fixed catastrophic init system bug that destroyed other Claude frameworks. Now includes context7, playwright, and sequential-thinking MCP servers for enhanced capabilities.

## 🙏 Acknowledgments

This project draws inspiration and prompts from:

- **[SuperClaude Framework](https://github.com/SuperClaude-Org/SuperClaude_Framework)** - Advanced AI persona system concepts
- **[CCPlugins](https://github.com/brennercruvinel/CCPlugins)** - Some excellent prompt inspiration