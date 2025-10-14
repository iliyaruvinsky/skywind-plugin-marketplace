# Changelog

All notable changes to the StatusLine Variations plugin will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2025-10-14

### Added
- Initial release of StatusLine Variations plugin
- Three statusline presets:
  - **Minimal**: Time and model only
  - **Developer**: Time, model, user, and git branch
  - **Detailed**: Full view with cost tracking
- PowerShell implementation for Windows
- Comprehensive README with usage examples
- DevOps best practices documentation
- Cost tracking integration
- Git branch awareness
- Real-time session monitoring

### Features
- Time display in 12-hour format (customizable)
- Model name display (e.g., "Sonnet 4.5")
- Username context
- Git branch tracking with fallback to "main"
- Cost monitoring in USD with 4 decimal precision
- Updates every ~300ms (Claude Code standard)
- Easy switching between variations

### Documentation
- Installation instructions (automatic and manual)
- Use case descriptions for each variation
- Customization examples
- Troubleshooting guide
- Platform compatibility notes
- DevOps best practices section
- JSON input field reference

### Technical
- PowerShell scripts with JSON parsing
- Git command integration
- Environment variable access
- Formatted output for different screen sizes
- Error handling with fallback values

## [Unreleased]

### Planned
- Bash versions for Linux/Mac support
- ANSI color-coded variations
- Session duration tracking
- Performance metrics display
- Compact variation for small terminals
- Multilingual label support
- Cost alert thresholds
- Custom theme support
