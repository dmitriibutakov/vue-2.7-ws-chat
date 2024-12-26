<template>
  <div class="p-4 h-screen flex flex-col">
    <form @submit.prevent="sendMessage" class="flex items-center gap-2 mb-4">
      <input
          v-model="message"
          class="flex-1 border border-gray-300 rounded p-2"
          type="text"
          data-testid="message-input"
          placeholder="Type your message..."
      />
      <button
          type="submit"
          class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-600"
          data-testid="send-button"
      >
        Send
      </button>
    </form>
    <textarea
        data-testid="chat-output"
        class="flex-1 border border-gray-300 rounded p-2 bg-white resize-none"
        readonly
    >
{{ chatLog }}
    </textarea>
  </div>
</template>

<script>
export default {
  name: "Chat",
  data() {
    return {
      message: "",
      chatLog: "",
      ws: null,
    };
  },
  methods: {
    sendMessage() {
      if (this.message.trim()) {
        const userMessage = this.message.trim();
        this.chatLog += `You: ${userMessage}\n`;
        this.ws.send(userMessage);
        this.message = "";
      }
    },
  },
  mounted() {
    this.ws = new WebSocket("wss://echo.websocket.org");
    this.ws.onmessage = (event) => {
      this.chatLog += `Server: ${event.data}\n`;
    };
  },
  beforeDestroy() {
    if (this.ws) {
      this.ws.close();
    }
  },
};
</script>

<style scoped>
@import url("https://unpkg.com/tailwindcss@^1.0/dist/tailwind.min.css");
</style>