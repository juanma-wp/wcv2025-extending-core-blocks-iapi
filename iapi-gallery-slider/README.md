# IAPI Gallery Slider

An interactive WordPress block that creates a gallery slider using the WordPress Interactivity API, compatible with core cover, image, and media-text blocks.

## Description

This plugin provides a custom gallery slider block that wraps around WordPress core blocks (cover, image, media-text) to create an interactive slideshow experience. It leverages the WordPress Interactivity API to provide smooth transitions, autoplay functionality, and navigation controls without requiring jQuery or other external libraries.

## Features

- **Core Block Compatibility**: Works seamlessly with WordPress core blocks:
  - Cover blocks
  - Image blocks
  - Media & Text blocks
- **Autoplay Support**: Configurable automatic slide progression
- **Continuous Loop**: Optional infinite scrolling through slides
- **Custom Speed Control**: Adjustable transition timing (1-10 seconds)
- **Navigation Controls**: Previous/Next buttons with keyboard support
- **Slide Counter**: Visual indicator showing current slide position
- **Smooth Transitions**: Built-in fade and slide effects
- **No External Dependencies**: Uses only WordPress Interactivity API

## Requirements

- WordPress 6.4 or higher
- PHP 7.0 or higher
- Gutenberg 16.2+ (for experimental Interactivity API features)

## Installation

### From Source

1. Clone or download to your plugins directory:
```bash
cd wp-content/plugins/
git clone [repository-url] iapi-gallery-slider
```

2. Install dependencies:
```bash
cd iapi-gallery-slider
npm install
```

3. Build the plugin:
```bash
npm run build
```

4. Activate in WordPress Admin → Plugins

## Usage

### Creating a Gallery Slider

1. In the Block Editor, add the "IAPI Gallery Slider" block
2. Inside the slider block, add any combination of:
   - Cover blocks (great for hero slides)
   - Image blocks (for simple image galleries)
   - Media & Text blocks (for content-rich slides)
3. Configure slider settings in the block sidebar:
   - **Autoplay**: Toggle automatic slide progression
   - **Continuous**: Enable infinite loop
   - **Speed**: Set transition interval (1-10 seconds)

### Example Structure

```
IAPI Gallery Slider
├── Cover Block (Slide 1)
├── Image Block (Slide 2)
├── Media & Text Block (Slide 3)
└── Cover Block (Slide 4)
```

### Block Settings

- **Autoplay** (boolean): Automatically advance slides
- **Continuous** (boolean): Loop back to first slide after reaching the last
- **Speed** (number): Seconds between automatic transitions (default: 3)

## Development

### Available Scripts

- `npm start` - Start development server with hot reloading
- `npm run build` - Build for production
- `npm run format` - Format code to WordPress standards
- `npm run lint:css` - Lint stylesheets
- `npm run lint:js` - Lint JavaScript
- `npm run packages-update` - Update WordPress packages
- `npm run plugin-zip` - Create distributable ZIP

### Project Structure

```
iapi-gallery-slider/
├── iapi-gallery-slider.php   # Main plugin file
├── src/
│   ├── block.json            # Block metadata
│   ├── index.js              # Block registration
│   ├── edit.js               # Editor component
│   ├── save.js               # Save function
│   ├── editor.scss           # Editor styles
│   ├── style.scss            # Frontend styles
│   ├── render.php            # Server-side rendering
│   ├── view.js               # Frontend interactivity
│   └── README.md             # Original template docs
└── build/                    # Compiled assets
```

## Technical Implementation

### Server-Side Processing

The plugin uses PHP's `WP_HTML_Tag_Processor` to:
1. Count total slides within the block
2. Add Interactivity API directives to each slide
3. Set up initial context with slide configuration
4. Initialize global state for the slider instance

### Interactivity API Integration

Frontend behavior is managed through:
- **State**: Tracks current slide, navigation status, and display text
- **Actions**: Handle next/previous navigation and autoplay toggling
- **Callbacks**: Initialize slides and manage autoplay intervals
- **Effects**: Automatic state updates based on user interactions

### Supported Directives

- `data-wp-interactive`: Namespace for the interactive region
- `data-wp-context`: Stores slider configuration
- `data-wp-init`: Initialize slide functionality
- `data-wp-on--click`: Handle navigation clicks
- `data-wp-bind--disabled`: Manage button states
- `data-wp-text`: Update slide counter dynamically

## Styling

The plugin includes default styles that can be customized via CSS:

```css
.wp-block-block-developer-cookbook-iapi-gallery-slider {
    /* Main slider container */
}

.wp-block-cover[data-wp-interactive="iapi-gallery"] {
    /* Individual slide styling */
}

/* Navigation buttons */
.slider-navigation button {
    /* Custom button styles */
}
```

## Browser Support

Compatible with all modern browsers supporting:
- ES6 modules
- CSS Grid and Flexbox
- WordPress Interactivity API

## Known Limitations

- Requires Gutenberg 16.2+ for Interactivity API support
- Not currently part of WordPress Core (experimental feature)
- Limited to specific core block types for slides

## Contributing

Contributions welcome! Please submit issues and pull requests on GitHub.

## License

GPL-2.0-or-later - See [LICENSE](https://www.gnu.org/licenses/gpl-2.0.html)

## Credits

- Author: Ryan Welcher
- Package: block-developer-cookbook
- Built with WordPress Interactivity API

## Resources

- [WordPress Interactivity API Proposal](https://make.wordpress.org/core/2023/03/30/proposal-the-interactivity-api-a-better-developer-experience-in-building-interactive-blocks/)
- [@wordpress/interactivity Package](https://github.com/WordPress/gutenberg/blob/trunk/packages/interactivity/README.md)
- [Interactivity API Discussions](https://github.com/WordPress/gutenberg/discussions/categories/interactivity-api)