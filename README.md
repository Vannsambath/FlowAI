# FlowAI

# Google Flow Video Automation Extension

A Chrome extension that automates video generation on Google Flow by processing multiple prompts from a text file and automatically downloading the generated videos.

## Features

- **Batch Processing**: Process multiple prompts from a single text file
- **Dual Format Support**: Handle both simple text prompts and JSON format prompts
- **Automatic Downloads**: Download generated videos with proper naming
- **Progress Tracking**: Real-time progress monitoring with pause/resume functionality
- **Error Handling**: Comprehensive error handling with retry mechanisms
- **User-Friendly Interface**: Clean sidebar interface with progress visualization

## Installation

1. Clone or download this repository
2. Open Chrome and navigate to `chrome://extensions/`
3. Enable "Developer mode" in the top right
4. Click "Load unpacked" and select the extension folder
5. The extension icon will appear in your Chrome toolbar

## Usage

1. Navigate to a Google Flow project page: `https://labs.google/fx/tools/flow/project/[project-id]`
2. Click the extension icon to open the sidebar
3. Select a `prompts.txt` file containing your prompts (one per line)
4. Click "Start Processing" to begin automation
5. Monitor progress and download status in the sidebar
6. Videos will be automatically downloaded when generation completes

## Prompt Formats

### Simple Text Prompts
```
A cat playing with a ball of yarn
A sunset over the ocean
A person walking in the rain
```

### JSON Format Prompts
```json
{"prompt": "A cat playing with a ball of yarn", "details": {"style": "cartoon", "duration": "5s"}}
{"prompt": "A sunset over the ocean", "details": {"mood": "peaceful", "colors": "warm"}}
{"prompt": "A person walking in the rain", "details": {"weather": "stormy", "time": "evening"}}
```

For JSON prompts, the extension will use the "prompt" field value as the video filename.

## File Structure

```
flowGoogle-extension/
├── manifest.json              # Extension manifest
├── background/
│   └── background.js         # Background service worker
├── content/
│   └── content.js           # Content script for Flow page interaction
├── popup/
│   ├── popup.html           # Sidebar interface
│   ├── popup.js             # Sidebar logic
│   └── popup.css            # Sidebar styling
├── utils/
│   ├── domHelpers.js        # DOM interaction utilities
│   └── promptParser.js      # Prompt parsing utilities
├── icons/
│   ├── icon16.png           # Extension icons
│   ├── icon48.png
│   └── icon128.png
└── README.md
```

## How It Works

1. **Content Script Injection**: The extension injects a content script into Google Flow pages
2. **DOM Interaction**: Uses robust selectors to interact with Flow's textarea and buttons
3. **Generation Monitoring**: Monitors progress indicators to detect when videos are ready
4. **Video Extraction**: Extracts video URLs from the generated content
5. **Automatic Downloads**: Uses Chrome's downloads API to save videos with proper names

## Technical Details

- **Manifest Version**: 3 (latest Chrome extension format)
- **Permissions**: `activeTab`, `downloads`, `storage`, `sidePanel`
- **Host Permissions**: `https://labs.google/*`
- **Content Script Injection**: Automatic injection on Flow project pages
- **Side Panel API**: Modern sidebar interface

## Settings

- **Delay Between Prompts**: Configurable delay between processing prompts (1-60 seconds)
- **Max Retries**: Number of retry attempts for failed prompts (0-5)
- **Auto Download**: Toggle automatic video downloading

## Error Handling

The extension includes comprehensive error handling for:
- Network timeouts
- DOM element detection failures
- Video generation failures
- Download errors
- File parsing errors

## Troubleshooting

### Extension Not Working
- Ensure you're on a Google Flow project page
- Check that the page has fully loaded
- Try refreshing the page and reopening the extension

### Videos Not Downloading
- Check Chrome's download settings
- Ensure sufficient disk space
- Verify download permissions in Chrome settings

### Prompts Not Processing
- Verify prompt file format (one prompt per line)
- Check for special characters that might cause issues
- Ensure prompts are within character limits

## Development

To modify or extend the extension:

1. Make changes to the source files
2. Reload the extension in `chrome://extensions/`
3. Test on a Google Flow project page

## Version History

- **v1.0.0**: Initial release with core automation features

## License

This project is for educational and personal use. Please respect Google's terms of service when using this extension.

## Support

For issues or questions, please check the troubleshooting section above or review the code comments for implementation details.
