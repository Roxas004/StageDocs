# PHPStan

This document outlines the best practices for using PHPStan for static analysis of your PHP code.

## 1. Configuration

PHPStan reads its configuration from the file `phpstan.neon.dist`. This file defines the analysis level, the paths to include and exclude, as well as other essential settings.

[PHPStan Config](../phpstan.dist.neon)

**Execution:**  
  - Run PHPStan from the command line:
    ```
    vendor/bin/phpstan analyse
    ```
  - To simplify the execution of PHPStan and other quality assurance tools, you have the option to run all QA commands using the makefile command:
    ```bash
    make apply-qa
    ```

## 2. Baseline
  - **What is it?**  
    The baseline is a file that lists the errors currently present in your code. It allows you to focus solely on new errors or regressions as your code evolves, disregarding issues that are already known.

  - **Advantages of using a baseline:**
    - **Focus on new issues:**  
      Errors recorded in the baseline are ignored in subsequent analyses, highlighting only newly introduced anomalies.
    - **Progressive improvement:**  
      This approach facilitates the gradual correction of existing errors, making continuous enhancement of your code quality more manageable.
    - **Continuous quality control:**  
      The baseline serves as a snapshot of your code’s state, ensuring that changes do not introduce new errors.
      
  - **Execution:**  
    To run PHPStan and generate the baseline simultaneously, use the following command:
    ```
    vendor/bin/phpstan analyse --generate-baseline=phpstan-baseline.neon
    ```

## 3. Best Practices

- **Analysis Level**: 
  - For new projects, directly use the `max` level to enforce best practices from the beginning.
  - For legacy projects, consider starting at a lower level and progressively increasing the strictness.
- **Folder Exclusion**: Exclude non-essential folders (such as `vendor`) to speed up the analysis.


