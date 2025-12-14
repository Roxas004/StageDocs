# QA - PHPInsights

PHPInsights is a static analysis tool that evaluates the overall quality of PHP code. It not only focuses on error detection but also on quality metrics such as cyclomatic complexity, maintainability, and adherence to coding standards.

## Objectives

- **Measure code quality**: Obtain metrics on complexity, readability, and maintainability.
- **Identify areas for improvement**: Detect methods or classes that are too complex and flag standard violations or anti-patterns.
- **Complement other QA tools**: PHPInsights provides an overall view of the code’s state by highlighting qualitative aspects.

## Configuration

PHPInsights can be configured via a `phpinsights.php` file located at the root of the project. This file allows you to adjust rules, exclude certain directories, or set specific thresholds.

[PHPInsights Config](../phpinsights.php)

## Usage

Launch PHPInsights from the root of your project by running the following command:

```bash
vendor/bin/phpinsights
```

To simplify the execution of PHPInsights and other quality assurance tools, you have the option to run all QA commands using the makefile command:
```bash
make apply-qa
```

## Interpreting the Results
The PHPInsights report provides several metrics:

- **Quality Score**: An overall rating based on various code quality metrics.
- **Complexity**: Indicates how complex the code is. High complexity might suggest the need for refactoring.
- **Style & Architecture**: Highlights coding standard violations and potential maintainability issues.
Use these results to prioritize refactoring efforts and improve code quality over time.

## Troubleshooting
Memory Exhaustion:
If you receive an error like "Allowed memory size exhausted", try increasing the PHP memory limit whit this command:
```
php -d memory_limit=512M vendor/bin/phpinsights
```

## Configuration Errors:
If errors occur regarding unknown configuration keys, verify that your `phpinsights.php` file only uses valid keys (min-quality, min-complexity, min-architecture, min-style, disable-security-check).

## Best Practices
- **Run regularly**: Execute PHPInsights on a regular basis to monitor code quality.
- **Integrate in CI/CD**: Add PHPInsights to your CI/CD pipeline for continuous feedback.
- **Review thresholds**: Adjust the configuration thresholds to suit your project's specific needs.
- **Analyze trends**: Track metrics over time and focus refactoring efforts where they count.

