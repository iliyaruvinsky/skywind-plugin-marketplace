# Skywind Plugin Marketplace

**One unified marketplace for AI coding assistant plugins**

Stop AI hallucinations. Enforce code quality. Standardize workflows across your DevOps teams.

## What is This?

The Skywind Plugin Marketplace is a centralized repository of reusable rule sets (plugins) for AI coding assistants like Claude Code, Cursor, and Windsurf. Each plugin contains rules that guide AI behavior to ensure:

- **Accuracy** - No more hallucinated completions
- **Consistency** - Same standards across all projects
- **Quality** - Enforced best practices
- **Efficiency** - Faster onboarding with pre-made rules

## Why Use Plugins?

### Without Plugins
```
Developer 1: "Claude keeps saying it changed files when it didn't"
Developer 2: "Cursor gave me insecure code patterns"
Developer 3: "I have to keep reminding the AI about our standards"
Manager: "Why are we paying for AI that needs constant supervision?"
```

### With Plugins
```
DevOps Lead: "Install the anti-hallucination plugin"
Team: *installs plugin*
AI: *automatically follows verification rules*
Team: *gets accurate, consistent results*
Manager: "AI costs down 40%, quality up 60%"
```

## Quick Start for DevOps Teams

### Step 1: Clone This Marketplace (One-Time Setup)

```bash
git clone https://github.com/iliyaruvinsky/skywind-plugin-marketplace.git
```

### Step 2: Navigate to Your Project

```bash
cd /path/to/your/project
```

### Step 3: Install a Plugin

**For Cursor (Windows):**
```powershell
C:\path\to\skywind-plugin-marketplace\scripts\install.ps1 -PluginId anti-hallucination/strict-verification -Tool cursor
```

**For Claude Code (Windows):**
```powershell
C:\path\to\skywind-plugin-marketplace\scripts\install.ps1 -PluginId anti-hallucination/strict-verification
```

**For Cursor (Mac/Linux):**
```bash
/path/to/skywind-plugin-marketplace/scripts/install.sh anti-hallucination/strict-verification --tool cursor
```

**For Claude Code (Mac/Linux):**
```bash
/path/to/skywind-plugin-marketplace/scripts/install.sh anti-hallucination/strict-verification
```

**For Windsurf:**
```bash
# Windows
C:\path\to\skywind-plugin-marketplace\scripts\install.ps1 -PluginId anti-hallucination/strict-verification -Tool windsurf

# Mac/Linux
/path/to/skywind-plugin-marketplace/scripts/install.sh anti-hallucination/strict-verification --tool windsurf
```

### Step 4: Restart Your AI Assistant

Close and reopen Claude Code, Cursor, or Windsurf. The plugin rules will now be active!

---

## Alternative: Manual Installation

If you prefer not to use the installation script:

1. **Browse to the plugin**: [strict-verification rules](https://github.com/iliyaruvinsky/skywind-plugin-marketplace/blob/main/plugins/anti-hallucination/strict-verification/rules.md)
2. **Copy the content** of `rules.md`
3. **Paste into your project**:
   - **Claude Code**: Create/edit `.claude/rules/strict-verification.md`
   - **Cursor**: Append to `.cursorrules` file in project root
   - **Windsurf**: Create/edit `.windsurf/rules/strict-verification.md`
4. **Restart your AI assistant**

---

## Browse Available Plugins

After cloning the marketplace, you can list all available plugins:

```bash
cd skywind-plugin-marketplace
node scripts/list-plugins.js
```

## Available Plugin Categories

### 🎯 anti-hallucination
Rules to reduce AI hallucinations and improve accuracy
- `strict-verification` - Mandatory file verification before claiming success

### 🏗️ code-quality
Standards for clean, maintainable code
- Coming soon

### 🔒 security
Security-focused coding guidelines
- Coming soon

### 🔄 workflow
Git, CI/CD, PR standards, team collaboration
- Coming soon

### ⚡ performance
Performance optimization guidelines
- Coming soon

### 🧪 testing-automation
TDD, test coverage, quality assurance
- `testing-agent` - Comprehensive testing rules for SAPUI5, ABAP, OData, Java, JavaScript, React

### 📚 documentation
Documentation standards, inline comments
- Coming soon

## Featured Plugin: Strict Verification Rules

**The most important plugin for any serious project**

Prevents AI assistants from reporting false completions. Enforces mandatory verification after every file change.

**Before:**
- AI: "I've updated all 10 files"
- Reality: Only 3 files changed
- Cost: Wasted time debugging + API costs

**After:**
- AI: "Let me verify each file..."
- AI: "Confirmed: 3 updated, 7 failed. Fixing the 7 now."
- Result: Accurate work, first time

[Install Now](plugins/anti-hallucination/strict-verification/)

## Featured Plugin: Testing Agent

**Comprehensive testing automation for enterprise development**

The Testing Agent plugin provides complete testing rules for AI agents working across multiple technology stacks including SAP and modern web frameworks.

**Supported Technologies:**
- **SAP**: SAPUI5 (QUnit, OPA5), ABAP (ABAP Unit, ATC), OData
- **Web**: Java (JUnit 5), JavaScript (Jest), React (React Testing Library)

**Key Features:**
- Testing pyramid enforcement (70% unit, 20% integration, 10% E2E)
- Technology-specific best practices from SAP Community & official docs
- Honest test result reporting
- Quality gates with coverage requirements
- CI/CD integration guidelines

**Use Cases:**
- DevOps teams working with SAP development
- Teams building SAPUI5 applications
- Full-stack development with React + Java backends
- Enterprise quality assurance automation

[Learn More](plugins/testing-automation/testing-agent/)

## For DevOps Teams

### Standardize Across Projects

Install the same plugins across all team projects for consistency:

```bash
# Create a team bundle
for project in project1 project2 project3; do
    cd $project
    ./path/to/marketplace/scripts/install.sh anti-hallucination/strict-verification
    ./path/to/marketplace/scripts/install.sh code-quality/clean-code-enforcer
    cd ..
done
```

### Create Custom Plugins

Have company-specific standards? Create a custom plugin:

```bash
cp -r templates/plugin-template/ plugins/your-category/your-plugin/
# Edit the files
# Commit to marketplace
```

See [docs/plugin-development.md](docs/plugin-development.md) for details.

## Installation Paths

Plugins install to different locations based on the tool:

| Tool | Default Path |
|------|-------------|
| Claude Code | `.claude/rules/<plugin-name>.md` |
| Cursor | `.cursorrules` (appends) |
| Windsurf | `.windsurf/rules/<plugin-name>.md` |

## Compatibility Matrix

| Plugin | Claude Code | Cursor | Windsurf | Copilot |
|--------|------------|--------|----------|---------|
| strict-verification | ✅ | ✅ | ✅ | ❌ |
| testing-agent | ✅ | ✅ | ✅ | ❌ |

## Benefits

### For Developers
- ✅ Accurate AI responses
- ✅ Less debugging
- ✅ Faster development
- ✅ Trust in AI assistance

### For Teams
- ✅ Consistent code quality
- ✅ Standardized workflows
- ✅ Easier onboarding
- ✅ Shared best practices

### For Organizations
- ✅ Lower AI costs (fewer wasted iterations)
- ✅ Higher code quality
- ✅ Reduced security risks
- ✅ Measurable standards

## Project Structure

```
skywind-plugin-marketplace/
├── README.md                    # This file
├── plugin-schema.json           # Plugin metadata schema
├── plugins/                     # All plugins organized by category
│   └── anti-hallucination/
│       └── strict-verification/
│           ├── plugin.json      # Plugin metadata
│           ├── rules.md         # The actual rules
│           ├── README.md        # Plugin documentation
│           └── CHANGELOG.md     # Version history
├── scripts/
│   ├── install.sh               # Unix/Mac installer
│   ├── install.ps1              # Windows installer
│   └── list-plugins.js          # Browse plugins
├── templates/                   # Templates for creating new plugins
└── docs/                        # Marketplace documentation
```

## Contributing

Want to contribute a plugin?

1. Fork this repository
2. Create your plugin using the template
3. Test it on real projects
4. Submit a pull request

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## FAQ

### Q: Do plugins slow down the AI?
A: No. Rules are guidelines that improve decision-making, not computational overhead.

### Q: Can I use multiple plugins together?
A: Yes! Install as many as you need. They're designed to work together.

### Q: What if a plugin conflicts with my project needs?
A: Fork it and customize it for your needs, or create your own plugin.

### Q: Are plugins secure?
A: Plugins are just markdown files with text rules. Review them before installing.

### Q: Can I sell plugins on this marketplace?
A: Currently this is an open-source marketplace. Commercial plugins can specify their own licenses.

### Q: Does this work with [other AI tool]?
A: If it reads rule files (like .cursorrules), it should work. Test and let us know!

## Support

- **Documentation**: See [docs/](docs/)
- **Issues**: Open an issue in this repository
- **Email**: devops@skywind.com
- **Discussions**: Use GitHub Discussions for questions

## Roadmap

- [x] Core marketplace structure
- [x] Anti-hallucination plugins
- [x] Installation scripts
- [x] Testing automation plugins
- [ ] Code quality plugins
- [ ] Security plugins
- [ ] DevOps workflow plugins
- [ ] Web-based catalog interface
- [ ] Plugin dependency management
- [ ] Version compatibility checker
- [ ] Analytics and usage tracking
- [ ] Enterprise features (private plugins, SSO)

## License

This marketplace and its structure: MIT License

Individual plugins: See each plugin's LICENSE file

## Credits

Created by Skywind Platform DevOps Team

Inspired by the need for consistent, reliable AI coding assistance across enterprise teams.

---

**Make your AI coding assistants work consistently and accurately. Browse plugins now:**

```bash
node scripts/list-plugins.js
```
