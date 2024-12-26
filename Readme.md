# Build a Simple Chat Component Using Vue.js 2.7 and WebSockets

Create a chat interface that allows users to type a message in an input box and send it to a WebSocket server.

## Requirements

1. The WebSocket server to use is `wss://echo.websocket.org`.
2. A message typed in the input should be sent to the WebSocket server when the "Send" button is clicked.
3. The response from the WebSocket server should be displayed in a textarea below the input field, appending each message.
4. Add a `"message-input"` `data-testid` attribute to the input field.
5. Add a `"send-button"` `data-testid` attribute to the "Send" button.
6. Add a `"chat-output"` `data-testid` attribute to the textarea where messages will be displayed.
7. Use Tailwind CSS or Bootstrap for basic styling.

## Hints

1. Ensure the WebSocket connection is properly closed when the component is destroyed.
2. The "Preview" tab will display your component for general testing purposes, but tests are the basis for scoring.
3. In Codility, you can't install Tailwind with npm. Instead, you can include it statically using a CDN link:  
   `https://unpkg.com/tailwindcss@^1.0/dist/tailwind.min.css`

## Available Packages/Libraries

1. **Vue.js**: 2.7.7
2. **Node.js**: 16