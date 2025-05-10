# Rails 8 Copilot Instructions

This repository contains specialized instruction files for GitHub Copilot to generate high-quality Rails 8 code following modern best practices. These instructions help ensure that AI-generated code follows consistent patterns and leverages the most current Rails features and ecosystem tools.

## Overview

This repository organizes detailed instructions for GitHub Copilot focused on modern Rails 8 application development. The instructions cover the Rails ecosystem including Hotwire (Turbo & Stimulus), Solid Queue for background jobs, Tailwind CSS for styling, Import Maps for JavaScript management, and Kamal for deployment.

## Structure

The repository is organized with specialized instruction files in the `.github/instructions/` directory:

- **[rails8.instructions.md](.github/instructions/rails8.instructions.md)** - Core Rails 8 conventions and best practices
- **[turbo-stimulus.instructions.md](.github/instructions/turbo-stimulus.instructions.md)** - Hotwire patterns and implementation guidelines
- **[solid-queue.instructions.md](.github/instructions/solid-queue.instructions.md)** - Background job processing with Solid Queue
- **[kamal.instructions.md](.github/instructions/kamal.instructions.md)** - Deployment configuration and practices
- **[tailwind.instructions.md](.github/instructions/tailwind.instructions.md)** - Styling guidelines with Tailwind CSS
- **[importmaps.instructions.md](.github/instructions/importmaps.instructions.md)** - JavaScript dependency management
- **[hotwire-native.instructions.md](.github/instructions/hotwire-native.instructions.md)** - Guidelines for Hotwire Native mobile apps

Each instruction file uses frontmatter to specify which files the instructions apply to, ensuring context-specific guidance.

## Usage

1. Copy this repository structure into your Rails 8 project
2. Customize the instruction files as needed for your specific project requirements
3. GitHub Copilot will use these instructions when generating code in files matching the patterns specified in each instruction's frontmatter

The main `[.github/copilot-instructions.md](.github/copilot-instructions.md)` file provides high-level guidance and references the specialized instruction files for deeper context.

## Technology Stack

These instructions are designed for applications using:

- Rails 8.0
- Ruby 3.3+
- Turbo & Stimulus (Hotwire)
- Solid Queue
- Kamal for deployment
- SQLite 
- Tailwind CSS
- Import Maps for JavaScript management

## Contributing

Feel free to submit pull requests to improve these instruction files as Rails 8 and its ecosystem evolve. Please ensure any additions maintain the structured, detailed approach of the existing instructions.

## License

This repository is available as open source under the terms of the MIT License.