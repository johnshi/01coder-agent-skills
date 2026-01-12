---
name: "Next.js Security Scan"
description: "Comprehensive security vulnerability scanner for Next.js and TypeScript/JavaScript projects. Detects OWASP Top 10 vulnerabilities, XSS, injection flaws, authentication issues, hardcoded secrets, and Next.js-specific security problems. Audits dependencies for known CVEs and generates actionable security reports."
---

# Next.js Security Scan Skill

This skill enables comprehensive security scanning of Next.js and TypeScript/JavaScript projects based on OWASP guidelines and industry best practices.

## When to Use This Skill

- Security audits of Next.js applications
- Code review for security vulnerabilities
- Pre-deployment security checks
- Dependency vulnerability assessment
- Detecting hardcoded secrets and credentials

## Scan Types

### 1. Quick Scan
Fast scan focusing on critical vulnerabilities:
- Hardcoded secrets and API keys
- Dangerous function usage (`dangerouslySetInnerHTML`, `eval`)
- Missing authentication in Server Actions
- Known vulnerable dependencies

### 2. Full Scan
Comprehensive security assessment covering:
- All OWASP Top 10:2025 categories
- XSS vulnerability patterns
- Injection vulnerabilities (SQL, NoSQL, Command)
- Authentication and authorization flaws
- Security misconfigurations
- Cryptographic failures
- Next.js-specific vulnerabilities
- Dependency audit (CVE check)
- Environment variable exposure

### 3. Targeted Scan
Focus on specific vulnerability categories:
- `--xss` - Cross-site scripting patterns
- `--injection` - SQL/NoSQL/Command injection
- `--auth` - Authentication/authorization issues
- `--secrets` - Hardcoded credentials
- `--deps` - Dependency vulnerabilities
- `--nextjs` - Next.js specific issues

## Scan Procedure

### Step 1: Project Discovery
1. Identify project type (Next.js App Router, Pages Router, or plain React)
2. Locate configuration files (`next.config.js`, `package.json`, `.env*`)
3. Map the codebase structure

### Step 2: Dependency Audit
Run the dependency audit script:
```bash
./scripts/dependency-audit.sh
```
Or manually:
```bash
npm audit --json
# or
yarn audit --json
```

### Step 3: Secret Scanning
Scan for hardcoded secrets:
```bash
python scripts/secret-scanner.py /path/to/project
```

### Step 4: Pattern Analysis
For each file in the codebase, check against patterns in:
- `references/xss-patterns.md` - XSS vulnerabilities
- `references/injection-patterns.md` - Injection flaws
- `references/auth-vulnerabilities.md` - Auth issues
- `references/nextjs-specific.md` - Next.js vulnerabilities

### Step 5: Report Generation
Generate a security report using:
- `assets/report-template.md` - Report structure

## Severity Classification

| Severity | Description | Action Required |
|----------|-------------|-----------------|
| CRITICAL | Exploitable vulnerability with severe impact | Immediate fix required |
| HIGH | Significant security risk | Fix before deployment |
| MEDIUM | Potential security issue | Fix in next release |
| LOW | Minor security concern | Consider fixing |
| INFO | Security best practice suggestion | Optional improvement |

## Key Files to Scan

### Always Check
- `**/*.ts`, `**/*.tsx`, `**/*.js`, `**/*.jsx` - Source code
- `next.config.js`, `next.config.mjs` - Next.js configuration
- `package.json`, `package-lock.json` - Dependencies
- `.env*` files - Environment variables
- `middleware.ts`, `middleware.js` - Middleware security

### High Priority Locations
- `app/api/**/*` - API routes (App Router)
- `pages/api/**/*` - API routes (Pages Router)
- `**/actions.ts`, `**/*-actions.ts` - Server Actions
- `lib/auth*`, `utils/auth*` - Authentication code
- `**/middleware.*` - Middleware files

## Output Format

Findings should be reported as:

```
[SEVERITY] Category: Description
  File: path/to/file.ts:lineNumber
  Code: <relevant code snippet>
  Risk: <explanation of the security risk>
  Fix: <recommended remediation>
```

## Integration with CI/CD

This skill can generate output compatible with:
- GitHub Security Advisories
- SARIF format for GitHub Code Scanning
- JSON for custom integrations

## References

Load additional context as needed:
- `references/owasp-top-10.md` - OWASP Top 10:2025 quick reference
- `references/xss-patterns.md` - XSS detection patterns
- `references/injection-patterns.md` - Injection vulnerability patterns
- `references/auth-vulnerabilities.md` - Authentication security patterns
- `references/nextjs-specific.md` - Next.js specific vulnerabilities and CVEs
