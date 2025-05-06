# IFTTT Webhook Resolver: Streamlined Webhook Automation for Node.js

## Project Overview

IFTTT Webhook Resolver is a lightweight Node.js module designed to simplify interactions with IFTTT (If This Then That) webhooks. The module provides a straightforward interface for sending custom trigger events to IFTTT, enabling developers to easily integrate IFTTT automation into their applications.

### Key Features
- Simple, one-method API for triggering IFTTT webhooks
- Supports up to three custom data values per webhook call
- SSL encrypted JSON payload transmission
- Promise-based asynchronous call mechanism
- Error handling and result tracking

### Purpose
The primary goal of this module is to abstract away the complexity of making IFTTT webhook calls. It allows developers to:
- Trigger custom events on IFTTT platforms
- Send dynamic data to IFTTT webhooks
- Integrate external services and applications with IFTTT automation

### Benefits
- Easy integration with minimal configuration
- Lightweight and dependency-efficient
- Provides a clean, intuitive interface for webhook interactions
- Supports cross-platform automation scenarios

## Getting Started, Installation, and Setup

### Prerequisites

- Node.js (version 10.x or higher recommended)
- npm (Node Package Manager)

### Installation

Install the package using npm:

```bash
npm install ifttt-webhook-resolver
```

### Quick Start

To use the IFTTT Webhook Resolver, you'll need:
- An IFTTT Webhooks API key
- A webhook action name

#### Basic Usage

```javascript
const IFTTTWebhook = require('ifttt-webhook-resolver');

// Example parameters
const webhookAction = 'my_webhook_trigger';
const apiKey = 'your_ifttt_webhooks_api_key';
const data = ['value1', 'value2', 'value3'];

IFTTTWebhook.call(webhookAction, apiKey, data)
  .then(response => {
    if (response.success) {
      console.log('Webhook triggered successfully');
    } else {
      console.error('Webhook trigger failed');
    }
  });
```

### Key Parameters

- `webhookAction`: The name of your IFTTT webhook trigger
- `apiKey`: Your IFTTT Webhooks service API key
- `data`: An array of values to pass to the webhook (max 3 values)

### Obtaining Your IFTTT Webhooks API Key

1. Go to IFTTT.com
2. Create a new Webhook applet
3. Navigate to Webhooks settings
4. Find your unique API key

### Troubleshooting

- Ensure you have a stable internet connection
- Verify your IFTTT Webhooks API key is correct
- Check that your webhook trigger name matches exactly

## API Reference

### Functions

#### `call(webhookAction, apiKey, data)`

Sends a webhook call to IFTTT with the specified parameters.

**Parameters:**
- `webhookAction` (string): The name of the IFTTT webhook trigger to invoke
- `apiKey` (string): Your IFTTT Webhooks API key
- `data` (array): An array of values to be passed to the webhook (max 3 values)

**Returns:**
- Promise resolving to an object with:
  - `success` (boolean): Indicates whether the webhook call was successful
  - `result` (object): The response from the IFTTT webhook

**Example Usage:**
```javascript
const iftttWebhook = require('ifttt-webhook-resolver');

// Send data to an IFTTT webhook
iftttWebhook.call('my_trigger', 'YOUR_API_KEY', ['value1', 'value2', 'value3'])
  .then(response => {
    if (response.success) {
      console.log('Webhook sent successfully');
    } else {
      console.error('Webhook failed', response.result);
    }
  });
```

**Notes:**
- The function automatically maps input data to `value1`, `value2`, etc. as required by IFTTT Webhooks
- Supports up to 3 values in the data array
- Uses the IFTTT Maker Webhooks endpoint at `https://maker.ifttt.com/trigger/`

## Project Structure

The project has a simple, straightforward structure with the following key files:

#### Core Files
- `index.js`: The main module file containing the core functionality for making IFTTT webhook calls
- `package.json`: Defines project metadata, dependencies, and npm script configurations

#### File Responsibilities
- `index.js`: Implements the `call` function that handles webhook actions to IFTTT
  - Transforms input data into IFTTT-compatible payload format
  - Sends POST requests to IFTTT Webhooks endpoint
  - Manages request and response handling

- `package.json`: Provides project configuration
  - Specifies module name and version
  - Defines project metadata and repository information
  - Declares main entry point as `index.js`

The project is designed as a lightweight npm module for interfacing with IFTTT Webhooks, with minimal file overhead.

## Technologies Used

### Programming Language
- JavaScript (Node.js)

### Core Libraries and Dependencies
- `request-promise`: HTTP request library for making webhook calls

### Platforms and Services
- IFTTT (If This Then That) Webhooks

### Development Tools
- Node.js runtime environment

### API Integration
- IFTTT Maker Webhooks API

## Additional Notes

### Webhook Configuration

The module interacts with IFTTT Webhooks, transforming input data into a format compatible with IFTTT's webhook endpoints. When making a call, input data is automatically mapped to `value1`, `value2`, etc., allowing flexible data transmission.

### Error Handling

The webhook resolver provides basic error handling with success/failure indicators. Calls return an object with:
- `success`: Boolean indicating whether the webhook call was successful
- `result`: Contains either the successful response or the error details

### Dependencies

Requires the `request-promise` package for making HTTP requests to the IFTTT Webhooks service.

### Security Considerations

The module requires an IFTTT API key for authentication. Ensure this key is kept confidential and not exposed in public repositories or client-side code.

### Limitations

- Currently supports sequential data mapping (up to available `valueN` fields)
- Relies on external IFTTT Webhooks service availability
- No built-in retry mechanism for failed requests

## Contributing

We welcome contributions to the IFTTT Webhook Resolver! Here are some guidelines to help you contribute effectively:

### How to Contribute

1. **Fork the Repository**: Create a fork of the project on GitHub.

2. **Create a Branch**: 
   - Create a new branch for your feature or bugfix
   - Use a clear and descriptive branch name
   - Example: `feature/add-error-handling` or `bugfix/resolve-connection-issue`

3. **Code Guidelines**:
   - Follow the existing code style in the project
   - Ensure your code is clean and well-commented
   - Use meaningful variable and function names

4. **Testing**:
   - Currently, no test suite is implemented
   - Manually test any changes thoroughly
   - Ensure that the core IFTTT webhook functionality remains intact

5. **Reporting Issues**:
   - Use the GitHub Issues section to report bugs or suggest enhancements
   - Provide detailed information about the issue
   - Include steps to reproduce, expected behavior, and actual behavior

6. **Pull Request Process**:
   - Ensure your code passes any existing checks
   - Provide a clear description of your changes
   - Link any related issues in the pull request description

### Important Notes

- The project uses `request-promise` for making HTTP requests
- Contributions should maintain the current simplicity of the webhook resolver
- Be mindful of the IFTTT webhook limitations (maximum of three value fields)

### Code of Conduct

- Be respectful and constructive
- Collaborate and provide helpful feedback
- Help maintain a welcoming community for all contributors

## License

The project is licensed under the ISC License. 

#### License Details
The ISC License is a permissive free software license published by the Internet Systems Consortium (ISC). It is functionally equivalent to the MIT license, but with simpler language.

For the full license text, please refer to the standard ISC License terms.