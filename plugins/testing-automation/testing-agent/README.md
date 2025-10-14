# Testing Agent Plugin

Comprehensive testing rules for AI coding agents working with enterprise SAP and modern web technologies. This plugin enforces testing best practices, test-driven development (TDD), and quality assurance standards across SAPUI5, ABAP, OData, Java, JavaScript, and React.

## Overview

The Testing Agent plugin provides a complete framework for AI agents to act as automated testing specialists. It includes rules, workflows, and standards derived from industry best practices and official SAP documentation.

## Key Features

- **Multi-Technology Support**: SAPUI5, ABAP, OData, Java, JavaScript, React
- **Testing Pyramid Enforcement**: Proper test distribution (70% unit, 20% integration, 10% E2E)
- **Framework-Specific Rules**: QUnit, ABAP Unit, JUnit, Jest, React Testing Library
- **Quality Gates**: Coverage requirements and definition of done
- **Honest Reporting**: Enforces truthful test result reporting
- **CI/CD Integration**: Pipeline-ready test execution guidelines

## Supported Technologies & Frameworks

### SAP Technologies

**SAPUI5**
- QUnit for unit testing
- OPA5 for integration testing
- UIVeri5 for E2E testing

**ABAP**
- ABAP Unit for unit testing
- ABAP Test Cockpit (ATC) for quality assurance
- eCATT for scenario testing

**OData**
- SAP Gateway Client (`/IWFND/GW_CLIENT`)
- Postman for API testing
- CRUD-Q operations validation

### Web Technologies

**Java**
- JUnit 5 for unit testing
- Mockito for mocking
- AssertJ for fluent assertions
- TestContainers for integration testing

**JavaScript**
- Jest or Vitest for testing
- Mocha + Chai as alternatives
- Sinon for mocks and stubs

**React**
- React Testing Library
- Jest or Vitest
- MSW for API mocking
- Cypress/Playwright for E2E

## Installation

### Automatic Installation

```bash
# Install from Skywind Plugin Marketplace
# (Requires marketplace configuration in project settings)
```

### Manual Installation for Claude Code

1. Copy `rules.md` to your `.claude/rules/` directory:
   ```bash
   cp rules.md .claude/rules/testing-agent-rules.md
   ```

2. The rules will be automatically loaded by Claude Code

### Manual Installation for Cursor

1. Append rules to `.cursorrules`:
   ```bash
   cat rules.md >> .cursorrules
   ```

### Manual Installation for Windsurf

1. Copy to Windsurf rules directory:
   ```bash
   cp rules.md .windsurf/rules/testing-agent-rules.md
   ```

## Usage

Once installed, the AI agent will automatically follow the testing rules when:

- Writing new code (will suggest tests)
- Reviewing code (will check test coverage)
- Debugging issues (will run and analyze tests)
- Implementing features (will follow TDD)
- Performing code reviews (will validate testing standards)

### Explicit Testing Commands

You can explicitly ask the agent to:

```
"Run all unit tests and report results"
"Create unit tests for the UserService class"
"Execute integration tests for the OData service"
"Check test coverage and identify gaps"
"Run E2E tests for the login flow"
"Generate a testing report"
```

## Testing Philosophy

### The Testing Pyramid

```
    /\
   /E2E\      10% - Critical user flows only
  /------\
 /Integration\ 20% - Component interactions
/------------\
/  Unit Tests \ 70% - Fast, isolated tests
```

### Core Principles

1. **Test First**: Consider testing before implementation
2. **Fast Feedback**: Tests should run in milliseconds to seconds
3. **Independence**: Each test must be isolated
4. **Honesty**: Never fake test results
5. **Maintainability**: Tests are code - treat them well

## Technology-Specific Quick Start

### SAPUI5 Example

```javascript
// Unit Test (QUnit)
QUnit.test("Should format currency correctly", function(assert) {
    // Arrange
    var oFormatter = new Formatter();

    // Act
    var result = oFormatter.formatCurrency(1234.56);

    // Assert
    assert.strictEqual(result, "1,234.56 EUR", "Currency formatted");
});

// Integration Test (OPA5)
opaTest("Should display user list", function(Given, When, Then) {
    Given.iStartMyApp();
    When.onTheMainPage.iPressTheUserButton();
    Then.onTheUserPage.iShouldSeeTheUserList();
});
```

### ABAP Example

```abap
CLASS ltc_calculator DEFINITION FOR TESTING
  DURATION SHORT RISK LEVEL HARMLESS.

  PRIVATE SECTION.
    DATA: cut TYPE REF TO zcl_calculator.

    METHODS: setup,
             test_addition FOR TESTING.
ENDCLASS.

CLASS ltc_calculator IMPLEMENTATION.
  METHOD setup.
    cut = NEW zcl_calculator( ).
  ENDMETHOD.

  METHOD test_addition.
    DATA(result) = cut->add( iv_a = 5 iv_b = 3 ).
    cl_abap_unit_assert=>assert_equals(
      act = result
      exp = 8
      msg = 'Addition should return 8' ).
  ENDMETHOD.
ENDCLASS.
```

### React Example

```javascript
import { render, screen } from '@testing-library/react';
import userEvent from '@testing-library/user-event';
import { UserProfile } from './UserProfile';

test('displays user name after loading', async () => {
  // Arrange
  render(<UserProfile userId="123" />);

  // Assert - loading state
  expect(screen.getByText(/loading/i)).toBeInTheDocument();

  // Assert - loaded state
  const userName = await screen.findByText(/john doe/i);
  expect(userName).toBeInTheDocument();
});
```

### Java Example

```java
import org.junit.jupiter.api.Test;
import static org.assertj.core.api.Assertions.assertThat;

class CalculatorTest {
    @Test
    void shouldAddTwoNumbers() {
        // Arrange
        Calculator calculator = new Calculator();

        // Act
        int result = calculator.add(5, 3);

        // Assert
        assertThat(result).isEqualTo(8);
    }
}
```

## Test Execution Workflow

The plugin guides agents through this workflow:

### 1. Analysis Phase
- Identify technology stack
- Review existing tests
- Identify coverage gaps

### 2. Creation Phase
- Write tests following standards
- Implement mocks and fixtures
- Follow naming conventions

### 3. Execution Phase
- Run unit tests first
- Run integration tests
- Execute E2E tests last
- Capture all results

### 4. Reporting Phase
```markdown
## Test Execution Report

### Summary
- Total Tests: 145
- Passed: 142
- Failed: 3
- Duration: 2.3s

### Coverage
- Line Coverage: 87%
- Branch Coverage: 78%

### Failed Tests
1. UserService.test.js:45 - Expected 200, got 404
2. ODataTest.abap - Assertion failed for field AMOUNT

### Recommendations
- Fix UserService endpoint configuration
- Update test data for AMOUNT field
```

## Quality Gates

### Minimum Requirements

Code is NOT deployment-ready unless:

- [ ] All unit tests pass (70%+ coverage)
- [ ] All integration tests pass
- [ ] Critical E2E tests pass
- [ ] No critical bugs or security issues
- [ ] ATC/Static analysis clean (SAP)
- [ ] Code review completed

### Coverage Targets

| Technology | Line Coverage | Branch Coverage |
|-----------|---------------|-----------------|
| Java | 80% | 70% |
| JavaScript/React | 80% | N/A |
| SAPUI5 | 70% | N/A |
| ABAP | 70% (100% critical) | N/A |

## Anti-Patterns to Avoid

The plugin enforces avoidance of:

1. ❌ Testing implementation details
2. ❌ Slow tests (> 100ms for unit tests)
3. ❌ Flaky tests
4. ❌ Test interdependence
5. ❌ Over-mocking
6. ❌ No assertions
7. ❌ One giant test
8. ❌ Ignoring failures
9. ❌ Testing private methods
10. ❌ Faking test results

## CI/CD Integration

### Pipeline Stages

**Pre-Commit**
```bash
npm run test:unit  # Fast unit tests only
```

**Commit/PR**
```bash
npm test           # All tests
npm run coverage   # Generate report
```

**Pre-Deployment**
```bash
npm run test:e2e   # End-to-end tests
npm run test:perf  # Performance tests
```

### Example GitHub Actions

```yaml
name: Test Pipeline

on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Install dependencies
        run: npm install
      - name: Run tests
        run: npm test
      - name: Generate coverage
        run: npm run coverage
      - name: Upload coverage
        uses: codecov/codecov-action@v2
```

## Common Testing Commands

### SAPUI5
```bash
npm run test              # All tests
npm run test:unit         # Unit tests only
npm run test:integration  # OPA5 tests
```

### ABAP
```abap
" Unit tests
SE80 -> Right-click -> Execute -> Unit Tests

" ATC
Transaction: ATC

" Mass execution
Program: RS_AUCV_RUNNER
```

### Java
```bash
mvn test                  # Run tests
mvn verify                # Tests + integration
mvn test -Dtest=ClassName # Specific test
```

### JavaScript/React
```bash
npm test                     # Run all tests
npm test -- --coverage       # With coverage
npm test -- --watch          # Watch mode
npm test MyComponent.test.js # Specific file
```

### OData
```
Transaction: /IWFND/GW_CLIENT

Test operations:
- GET    - Read entities
- POST   - Create entities
- PUT    - Update entities
- DELETE - Delete entities
- $filter, $expand, $select
```

## Troubleshooting

### Tests Are Slow
- Use in-memory databases
- Mock external dependencies
- Run tests in parallel
- Profile and optimize bottlenecks

### Tests Are Flaky
- Add proper async waits
- Ensure test independence
- Use fixed random seeds
- Mock time-dependent code

### Low Coverage
- Add tests for uncovered branches
- Test error paths
- Cover edge cases
- Remove dead code

### Tests Fail in CI but Pass Locally
- Check environment differences
- Verify test data setup
- Review async timing
- Check resource cleanup

## Best Practices Summary

### DO ✅
- Write tests first (TDD)
- Keep tests small and focused
- Use meaningful test names
- Follow AAA pattern (Arrange-Act-Assert)
- Mock external dependencies
- Test behavior, not implementation
- Run tests frequently
- Maintain tests like production code

### DON'T ❌
- Skip writing tests
- Test framework code
- Make tests depend on each other
- Use sleep/wait unnecessarily
- Ignore failing tests
- Test private methods directly
- Hard-code production data
- Fake test results

## Examples and Templates

See the `examples/` directory for:
- Sample test files for each technology
- Test report templates
- CI/CD configuration examples
- Mock and fixture patterns

## Contributing

Contributions to improve testing rules are welcome:

1. Fork the repository
2. Create a feature branch
3. Add your improvements
4. Submit a pull request

## Resources and References

### Official Documentation
- [SAPUI5 Testing](https://sapui5.hana.ondemand.com/)
- [ABAP Unit](https://help.sap.com/doc/abapdocu_latest_index_htm/latest/en-US/index.htm?file=abenabap_unit.htm)
- [JUnit 5](https://junit.org/junit5/docs/current/user-guide/)
- [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)
- [Jest](https://jestjs.io/)

### Community Resources
- [SAP Community - Testing](https://community.sap.com/)
- [Testing JavaScript](https://testingjavascript.com/)
- [Modern JavaScript Testing Best Practices](https://github.com/goldbergyoni/javascript-testing-best-practices)

## License

MIT License - See LICENSE file for details

## Author

Skywind Platform DevOps Team
- Email: devops@skywind.com
- Repository: https://github.com/iliyaruvinsky/skywind-plugin-marketplace

## Version History

See CHANGELOG.md for detailed version history.

---

**Remember**: The goal isn't just to write tests - it's to build confidence in your code and catch bugs before they reach production. This plugin helps AI agents become reliable testing partners in your development process.
