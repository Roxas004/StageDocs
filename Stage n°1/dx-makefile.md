# Makefile

This document provides a general overview of the features and commands associated with a Makefile.

## Purpose

A Makefile automates repetitive tasks such as compilation, testing, cleaning up temporary files, etc. With defined targets, multiple commands can be executed with a single command.

## Basic Syntax

A Makefile is structured with targets and dependencies. Here is the basic syntax:

```
target: dependency1 dependency2 ...
    command1
    command2
```

Example:
```
phpstan:
    @echo "Running PHPStan..."
    ./vendor/bin/phpstan analyse --configuration=phpstan.dist.neon
```

- **target**: the name of the task you want to execute.
- **dependencies** (optional): indicate which files or tasks need to be up-to-date before executing the command.
- **commands**: one or several command lines executed to perform the task. These lines must begin with a tab.

## Examples of Common Targets

### `all`

The default target that compiles or prepares the entire project.

```
all: build
    @echo "Build completed."
```

### `build`

Target to generate the project’s artifacts (compilation, assembling, etc.).

```
build:
    @echo "Building the project..."
    # Compilation commands here
```

### `clean`

Target to remove intermediate or temporary files generated during compilation.

```
clean:
    @echo "Cleaning up temporary files..."
    # Cleanup commands here
```

### `test`

Target to execute the project's unit tests.

```
test:
    @echo "Running tests..."
    # Commands to run tests here
```

## Usage

To use the Makefile, simply run the command `make` followed by the name of the target. For example:

```
make build
```

If you run `make` without specifying a target, the first target listed in the file will be executed.

## Tips
- Use the `help` target to list and describe all available targets.
    ```
    make help
    ```

    This will display:
    ```  
    Available targets:
    all     - Compile and build the project
    build   - Build the project
    clean   - Clean temporary files
    test    - Run unit tests
    ```
    
    Note that this is just an example based on the guidelines provided above.

    