# Agent Skills

A collection of custom skills for Claude Code, Anthropic's official CLI for Claude. These skills extend Claude Code's capabilities with specialized, domain-specific functionality.

## What are Agent Skills?

Agent skills are modular extensions that provide Claude Code with specialized knowledge and tools for specific tasks. Each skill includes:

- **SKILL.md** - Skill definition with instructions and procedures
- **References** - Domain knowledge and pattern libraries
- **Scripts** - Automation tools and utilities
- **Assets** - Templates and supporting files

## Available Skills

### Next.js Security Scan

A comprehensive security vulnerability scanner for Next.js and TypeScript/JavaScript projects.

**Features:**
- OWASP Top 10:2025 vulnerability detection
- XSS and injection flaw identification
- Authentication and authorization issue detection
- Hardcoded secrets and credentials scanning
- Next.js-specific vulnerability checks
- Dependency audit for known CVEs
- Actionable security reports

**Scan Types:**
- **Quick Scan** - Fast scan for critical vulnerabilities
- **Full Scan** - Comprehensive security assessment
- **Targeted Scan** - Focus on specific vulnerability categories (XSS, injection, auth, secrets, deps, nextjs)

**Usage:**
```
/nextjs-security-scan
```

## Project Structure

```
agent-skills/
├── skills/
│   └── nextjs-security-scan/
│       ├── SKILL.md              # Skill definition
│       ├── references/           # Vulnerability pattern libraries
│       │   ├── owasp-top-10.md
│       │   ├── xss-patterns.md
│       │   ├── injection-patterns.md
│       │   ├── auth-vulnerabilities.md
│       │   └── nextjs-specific.md
│       ├── scripts/              # Automation tools
│       │   ├── dependency-audit.sh
│       │   ├── secret-scanner.py
│       │   └── pattern-scanner.py
│       └── assets/               # Templates
│           └── report-template.md
├── .claude/                      # Claude Code configuration
├── LICENSE
└── README.md
```

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/sugarforever/agent-skills.git
   ```

2. Add the skills directory to your Claude Code configuration, or copy individual skills to your project's `.claude/skills/` directory.

## Creating New Skills

To create a new skill:

1. Create a new directory under `skills/` with your skill name
2. Add a `SKILL.md` file with:
   - YAML frontmatter (name, description)
   - Usage instructions
   - Procedures and workflows
3. Add supporting files as needed:
   - `references/` - Domain knowledge
   - `scripts/` - Automation tools
   - `assets/` - Templates and resources

## Requirements

For the Next.js Security Scan skill:
- Python 3.x (for secret scanner)
- Node.js and npm/yarn/pnpm (for dependency audit)
- jq (for JSON parsing in audit script)

## License

MIT License - see [LICENSE](LICENSE) for details.

## Contributing

Contributions are welcome! Please feel free to submit pull requests with new skills or improvements to existing ones.
