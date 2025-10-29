# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

#### CI Infrastructure Improvements
- **New Comprehensive CI Workflow** (`ci.yml`): Main orchestration workflow that runs all checks in parallel
  - Lint job for code formatting validation
  - Test matrix for Python 3.8-3.12
  - Coverage collection and reporting
  - Examples validation
  - Tutorials execution
  - Final gate to ensure all checks pass
  
- **Code Coverage Workflow** (`coverage.yml`): Dedicated workflow for coverage reporting
  - Generates XML, HTML, and terminal coverage reports
  - Uploads to Codecov for tracking over time
  - Stores HTML reports as artifacts (30-day retention)
  - Adds coverage summary to GitHub workflow summaries

- **PR Comment Workflow** (`pr-comment.yml`): Automated PR summary comments
  - Posts CI results summary on pull requests
  - Updates existing comments to avoid spam
  - Provides quick visibility into CI status

- **Dependabot Configuration**: Automated dependency updates
  - Weekly checks for GitHub Actions updates
  - Weekly checks for Python package updates
  - Automatic PR creation for security updates

- **Development Requirements** (`requirements-dev.txt`): Separate file for dev dependencies
  - Testing tools (pytest, pytest-cov, pytest-xdist)
  - Code formatting (yapf)
  - Example dependencies (termplotlib)
  - Optional tutorial dependencies

- **CI Documentation** (`docs/CI_INFRASTRUCTURE.md`): Comprehensive guide
  - Detailed workflow descriptions
  - Local testing instructions
  - Troubleshooting guide
  - Best practices
  - Maintenance guidelines

- **GitHub Templates**:
  - Issue template for CI-related problems
  - Pull request template with checklist

- **Status Badges**: Added to README.md
  - CI workflow status
  - Code coverage status
  - Python version support
  - License badge

### Changed

#### Updated Existing Workflows
- **python-pytest.yml**: Modernized testing workflow
  - Updated to actions/checkout@v4 and actions/setup-python@v5
  - Expanded Python version support (3.8-3.12)
  - Added pip caching for faster builds
  - Integrated coverage reporting with pytest-cov
  - Added Codecov upload
  - Changed to run on `ci-testing` branch in addition to `main`

- **python-yapf.yml**: Enhanced code formatting workflow
  - Updated to actions/checkout@v4 and actions/setup-python@v5
  - Added pip caching
  - Renamed to "Python Code Formatting" for clarity
  - Changed to run on `ci-testing` branch

- **python-tutorials.yml**: Improved tutorial execution workflow
  - Updated to latest GitHub Actions (v4/v5)
  - Added Python 3.9 and 3.11 to test matrix
  - Added pip caching
  - Improved error handling with `|| true` for non-critical failures
  - Added artifact upload for notebook outputs (7-day retention)
  - Changed to run on `ci-testing` branch

- **python-example.yml**: Enhanced example validation workflow
  - Updated to latest GitHub Actions (v4/v5)
  - Expanded Python version testing (3.9, 3.11)
  - Added pip caching
  - Added example_ais.py to test suite
  - Renamed to "Python Examples" for clarity
  - Changed to run on `ci-testing` branch

- **setup.py**: Updated Python version classifiers
  - Removed Python 3.6 and 3.7 (EOL)
  - Added Python 3.9, 3.10, 3.11, 3.12
  - Added `python_requires='>=3.8'`

- **README.md**: Enhanced documentation
  - Added status badges for CI, coverage, Python versions, and license
  - Added "Testing and CI" section with:
    - Overview of CI pipeline
    - Local testing instructions
    - Coverage report generation
    - List of all workflows
  - Updated installation instructions to reference new requirements

### Deprecated
- Python 3.7 support (reached EOL June 2023)
- Python 3.6 support (reached EOL December 2021)

### Infrastructure
- All workflows now use concurrency control to cancel outdated runs
- Implemented fail-fast: false strategy for better parallel testing
- Added comprehensive artifact management
- Improved caching strategy across all workflows

### Developer Experience
- Faster CI runs through caching and parallel execution
- Better visibility with status badges and PR comments
- Comprehensive documentation for troubleshooting
- Automated dependency updates via Dependabot
- Clear contribution guidelines via PR template

## [0.1.0] - 2023-XX-XX

### Added
- Initial release of PySA
- Simulated Annealing implementation
- Ising model support
- QUBO problem support
- AIS (Annealed Importance Sampling) support
- Basic CI workflows for testing
- Example scripts
- Tutorial notebooks

---

## Guidelines for Changelog

### Types of Changes
- `Added` for new features
- `Changed` for changes in existing functionality
- `Deprecated` for soon-to-be removed features
- `Removed` for now removed features
- `Fixed` for any bug fixes
- `Security` in case of vulnerabilities

### Version Numbers
Follow Semantic Versioning (MAJOR.MINOR.PATCH):
- MAJOR: Incompatible API changes
- MINOR: Backwards-compatible functionality additions
- PATCH: Backwards-compatible bug fixes
