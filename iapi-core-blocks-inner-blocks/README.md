# IAPI Core Blocks Inner Blocks


A WordPress plugin that extends core button and video blocks with interactive functionality using the WordPress Interactivity API.

<img width="9341" height="5939" alt="image" src="https://github.com/user-attachments/assets/8e70eb3e-3b2d-4a7a-b60b-9099c6294bd0" />

_[See excalidraw diagram](https://excalidraw.com/#json=aXJsuK0WiHkWRCENrsRE0,UQW4RAf7qWGadcZMGXMnTA)_

## Live Demo

[**Try the live demo**](https://playground.wordpress.net/?blueprint-url=https://raw.githubusercontent.com/juanma-wp/wcv2025-extending-core-blocks-iapi/refs/heads/main/iapi-core-blocks-inner-blocks/_playground/blueprint.json) - Experience the interactive blocks in a WordPress Playground environment.


## Description

This plugin demonstrates how to add interactive behavior to existing WordPress core blocks without modifying their structure. It specifically enhances button and video blocks to work together, allowing buttons to control video playback through the WordPress Interactivity API.

## Features

- **Interactive Buttons**: Transform regular button blocks into play/pause controls
- **Video Control Integration**: Connect buttons to video blocks for media control
- **Dynamic Text Updates**: Button text changes based on playback state (Play/Pause)
- **Server-Side Enhancement**: Uses WordPress filters to add interactivity without client-side block modifications
- **Lightweight Implementation**: No jQuery or external dependencies
- **Seamless Integration**: Works with existing core blocks without breaking changes

## Requirements

- WordPress 6.1 or higher
- PHP 7.0 or higher
- Node.js 16+ and npm for building

## Installation

### Build from Source

1. Clone or download to your plugins directory:
```bash
cd wp-content/plugins/
git clone [repository-url] iapi-core-blocks-inner-blocks
```

2. Install dependencies:
```bash
cd iapi-core-blocks-inner-blocks
npm install
```

3. Build the plugin:
```bash
npm run build
```

4. Activate the plugin in WordPress Admin → Plugins

## Usage

### Creating Interactive Video Controls

1. **Add the Container Block**:
   - Insert the "IAPI Core Blocks Inner Blocks" container block

2. **Add a Video Block**:
   - Inside the container, add a core Video block
   - Upload or select your video
   - Add the class `interactive-block--video` to the video block (in Advanced → Additional CSS Classes)

3. **Add Control Buttons**:
   - Add a core Button block
   - Set the button text (e.g., "Play")
   - Add the class `interactive-block--button-play` to the button block
   - The button will automatically control the video playback

### Example Block Structure

```
IAPI Core Blocks Inner Blocks (Container)
├── Video Block (with class: interactive-block--video)
└── Button Block (with class: interactive-block--button-play)
```

### CSS Classes

The plugin recognizes these special CSS classes:

- `interactive-block--video` - Marks a video block for interactive control
- `interactive-block--button-play` - Transforms a button into a play/pause control

## Development

### Available Scripts

- `npm start` - Start development with hot reloading
- `npm run build` - Build for production
- `npm run format` - Format code using WordPress standards
- `npm run lint:css` - Lint CSS files
- `npm run lint:js` - Lint JavaScript files
- `npm run packages-update` - Update WordPress packages
- `npm run plugin-zip` - Create plugin ZIP for distribution

### Project Structure

```
iapi-core-blocks-inner-blocks/
├── plugin.php              # Main plugin file with filters
├── src/
│   ├── block.json         # Block metadata
│   ├── index.js           # Block registration
│   ├── edit.js            # Editor interface
│   ├── save.js            # Save function
│   ├── editor.scss        # Editor styles
│   ├── style.scss         # Frontend styles
│   └── view.js            # Frontend interactivity logic
├── _playground/           # Testing environment
└── build/                 # Compiled assets
```

## Technical Implementation

### How It Works

1. **Block Registration**: The plugin registers a container block that provides the interactive context
2. **Filter Hooks**: Uses WordPress render_block filters to modify core blocks:
   - `render_block_core/button` - Adds click handlers and dynamic text
   - `render_block_core/video` - Adds watch callbacks for playback control
3. **HTML Processing**: Uses `WP_HTML_Tag_Processor` to safely modify block HTML
4. **Interactivity API**: Implements state management and event handling on the frontend

### Interactivity API Implementation

The plugin uses these Interactivity API features:

#### Directives
- `data-wp-interactive` - Defines the interactive namespace
- `data-wp-context` - Stores component state (playing status, button text)
- `data-wp-on--click` - Handles button click events
- `data-wp-text` - Updates button text dynamically
- `data-wp-watch` - Monitors and responds to state changes

#### State Management
```javascript
{
  isPlaying: false,        // Current playback state
  buttonText: "Play",      // Dynamic button label
  videoElement: null       // Reference to video element
}
```

#### Actions
- `playOrStop` - Toggles video playback
- `updateButtonText` - Updates button label based on state

#### Callbacks
- `initVideo` - Initializes video element reference
- `playOrStopVideo` - Handles actual video playback control

## Customization

### Styling

Add custom styles by targeting these selectors:

```css
/* Container block */
.wp-block-iapi-core-blocks-inner-blocks {
    /* Your styles */
}

/* Interactive video */
.interactive-block--video {
    /* Video styling */
}

/* Play/pause button */
.interactive-block--button-play {
    /* Button styling */
}
```

### Extending Functionality

You can extend this plugin by:
1. Adding more interactive block types
2. Creating additional control buttons (volume, fullscreen, etc.)
3. Adding support for audio blocks
4. Implementing playlist functionality

## Performance Considerations

- **Lightweight**: Minimal JavaScript footprint
- **Lazy Loading**: Scripts only load when interactive blocks are present
- **No Polling**: Uses efficient event-driven updates
- **Server-Side Processing**: Initial setup happens during PHP rendering

## Browser Compatibility

Works with all modern browsers supporting:
- ES6 modules
- HTML5 video API
- WordPress Interactivity API

## Troubleshooting

### Video Not Responding to Button
- Ensure the video block has the class `interactive-block--video`
- Verify the button has the class `interactive-block--button-play`
- Check that both blocks are inside the IAPI container block

### Button Text Not Updating
- Confirm the Interactivity API scripts are loading
- Check browser console for JavaScript errors
- Ensure WordPress and plugin are up to date

## Contributing

We welcome contributions! Please:
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a pull request

## License

GPL-2.0-or-later - See [LICENSE](https://www.gnu.org/licenses/gpl-2.0.html)

## Credits

Created by The WordPress Contributors as a demonstration of extending core blocks with the WordPress Interactivity API.

## Support

For issues, questions, or feature requests, please use the GitHub issue tracker.

## Related Resources

- [WordPress Interactivity API Documentation](https://developer.wordpress.org/block-editor/reference-guides/interactivity-api/)
- [Block Editor Handbook](https://developer.wordpress.org/block-editor/)
- [Extending Core Blocks Guide](https://developer.wordpress.org/block-editor/how-to-guides/block-tutorial/extending-core-blocks/)
