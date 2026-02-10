# GitHub Copilot Instructions

## GitHub CLI (gh) Usage

**Important:** Shell escaping in zsh doesn't work reliably when passing multi-line strings or complex text directly to `gh` commands. Always write PR/issue descriptions to a temporary file first, then reference the file.

### Best Practice

Instead of:
```bash
gh pr create --title "Title" --body "Multi-line
description with special characters"
```

Do this:
```bash
# Write description to temporary file
cat > .tmp/pr-description.md << 'EOF'
Multi-line description
with special characters
EOF

# Use the file
gh pr create --title "Title" --body-file .tmp/pr-description.md
```

### Temporary Files

- Use `.tmp/` directory for temporary files (e.g., PR descriptions, issue bodies)
- This directory is gitignored and safe for temporary content
- Clean up files after use if needed, or leave them for debugging
