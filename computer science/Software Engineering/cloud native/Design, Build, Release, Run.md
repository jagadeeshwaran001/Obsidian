## **Design**

- Determine Technology, dependencies, and tools for specific application features.
## Build Stage

- Compile and package the codebase with dependency, creating a immutable [[artifact]] (build). Unique identification of the build artifact is essential.
## Release Stage

- Combine the Build with specific [[deployment]] [[configuration]]. Each release is immutable and uniquely identifiable, such as through sematic versioning like (6.5.1) or timestamp (2025-08-15_22:00). Central repository storage facilitates the easy access, Including the [[rollback]] if needed.
## Run Stage

- Execute the application in the designed runtime environment using a specific release.

