# WCv2025 Extending Core Blocks with Interactivity API

A collection of WordPress plugins demonstrating how to extend core blocks using the Interactivity API, prepared for WordCamp presentations in 2025.

## Overview

This repository contains three WordPress plugins that showcase different approaches to extending WordPress core blocks with interactive functionality using the WordPress Interactivity API:

1. **Word Switcher Core Blocks** - Adds dynamic word switching functionality to paragraph and heading blocks
2. **IAPI Gallery Slider** - Creates an interactive gallery slider block with autoplay and navigation features
3. **IAPI Core Blocks Inner Blocks** - Extends core button and video blocks with interactive play/pause functionality

## Prerequisites

- WordPress 6.4+ (6.7+ recommended for Word Switcher)
- PHP 7.4+
- Node.js 16+ and npm
- WordPress development environment (Local, wp-env, etc.)

## Installation

### Clone the Repository

```bash
git clone https://github.com/yourusername/wcv2025-extending-core-blocks-iapi.git
cd wcv2025-extending-core-blocks-iapi
```

### Install Each Plugin

Each plugin needs to be built separately:

#### Word Switcher Core Blocks
```bash
cd word-switcher-core-blocks
npm install
npm run build
```

#### IAPI Gallery Slider
```bash
cd ../iapi-gallery-slider
npm install
npm run build
```

#### IAPI Core Blocks Inner Blocks
```bash
cd ../iapi-core-blocks-inner-blocks
npm install
npm run build
```

### Activate in WordPress

1. Copy each plugin folder to your WordPress `/wp-content/plugins/` directory
2. Navigate to WordPress Admin → Plugins
3. Activate the desired plugins

## Development

Each plugin can be developed independently with hot reloading:

```bash
cd [plugin-directory]
npm start
```

### Available Scripts

- `npm run build` - Build the plugin for production
- `npm start` - Start development server with hot reloading
- `npm run format` - Format code using WordPress coding standards
- `npm run lint:js` - Lint JavaScript files
- `npm run lint:css` - Lint CSS files
- `npm run plugin-zip` - Create a distributable ZIP file

### WordPress Environment (word-switcher-core-blocks)

The Word Switcher plugin includes wp-env configuration:

- `npm run env:start` - Start WordPress development environment
- `npm run env:stop` - Stop the environment
- `npm run env:destroy` - Remove the environment
- `npm run env:reset` - Reset the environment

## Plugin Details

### Word Switcher Core Blocks

Extends paragraph and heading blocks to add dynamic word switching functionality. Words cycle through a comma-separated list with fade transitions.

**Key Features:**
- Format type registration for block editor
- Server-side rendering with HTML Tag Processor
- Smooth fade transitions between words
- Works with paragraph and heading blocks

### IAPI Gallery Slider

Creates an interactive gallery slider that works with cover, image, and media-text blocks.

**Key Features:**
- Autoplay functionality
- Continuous/infinite loop option
- Customizable transition speed
- Navigation controls
- Slide counter display

### IAPI Core Blocks Inner Blocks

Demonstrates extending core blocks with interactive controls.

**Key Features:**
- Adds play/pause functionality to video blocks
- Creates interactive buttons for media control
- Uses WordPress Interactivity API for state management
- Seamless integration with existing blocks

## Technology Stack

- **WordPress Interactivity API** - For creating interactive frontend experiences
- **WordPress Block Editor (Gutenberg)** - For block development
- **@wordpress/scripts** - Build tooling and scripts
- **PHP HTML Tag Processor** - For server-side HTML manipulation
- **ES Modules** - Modern JavaScript module system

## Resources

- [WordPress Interactivity API Documentation](https://developer.wordpress.org/block-editor/reference-guides/interactivity-api/)
- [Block Editor Handbook](https://developer.wordpress.org/block-editor/)
- [WordPress Coding Standards](https://developer.wordpress.org/coding-standards/)

## Contributing

Contributions are welcome! Please feel free to submit issues and pull requests.

## License

All plugins are licensed under GPL-2.0-or-later.

## Author

The WordPress Contributors

## Presentation

These plugins were created as demonstration materials for WordCamp presentations about extending WordPress core blocks with the Interactivity API.