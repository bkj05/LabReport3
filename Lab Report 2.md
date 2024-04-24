# Lab Report 2 - Servers and SSH Keys (Week 3)

## Part 1: ChatServer

```java
import java.io.IOException;
import java.io.OutputStream;
import java.net.InetSocketAddress;
import java.net.URI;

import com.sun.net.httpserver.HttpExchange;
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpServer;

interface URLHandler {
    String handleRequest(URI url) throws Exception;
}

class ChatServerHandler implements HttpHandler {
    private static String chatMessages = "";

    public String handleRequest(URI url) throws Exception {
        String query = url.getQuery();
        String[] params = query.split("&");
        String user = null;
        String message = null;
        for (String param : params) {
            String[] keyValue = param.split("=");
            if (keyValue.length == 2) {
                if (keyValue[0].equals("s")) {
                    message = keyValue[1];
                } else if (keyValue[0].equals("user")) {
                    user = keyValue[1];
                }
            }
        }
        if (user != null && message != null) {
            chatMessages += user + ": " + message + "\n";
            return chatMessages;
        } else {
            throw new IllegalArgumentException("Invalid request parameters");
        }
    }

    @Override
    public void handle(HttpExchange exchange) throws IOException {
        try {
            String ret = handleRequest(exchange.getRequestURI());
            exchange.sendResponseHeaders(200, ret.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(ret.getBytes());
            os.close();
        } catch(Exception e) {
            String response = e.toString();
            exchange.sendResponseHeaders(400, response.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(response.getBytes());
            os.close();
        }
    }
}

public class ChatServer {
    public static void start(int port) throws IOException {
        HttpServer server = HttpServer.create(new InetSocketAddress(port), 0);
        server.createContext("/add-message", new ChatServerHandler());
        server.start();
        System.out.println("ChatServer started! Access it locally from a browser using http://localhost:" + port + "/add-message?s=YourMessage&user=YourUser");
    }

    public static void main(String[] args) throws IOException {
        int port = 8000;
        start(port);
    }
}

## Part 1: ScreenShots

- **Screenshot 1:** Adding "Hello" from user "jpolitz"
![Screenshot 1](screenshot1.png)
- **Methods called**: `handleRequest`, `sendResponseHeaders`, `getResponseBody`, `close`
- **Relevant arguments**: URI with query parameters `s=Hello&user=jpolitz`
- **Changes in class fields**: The `chatMessages` field is updated to "jpolitz: Hello\n"

- **Screenshot 2:** Adding "How are you" from user "yash"
![Screenshot 2](screenshot2.png)
- **Methods called**: `handleRequest`, `sendResponseHeaders`, `getResponseBody`, `close`
- **Relevant arguments**: URI with query parameters `s=How are you&user=yash`
- **Changes in class fields**: The `chatMessages` field is updated to "jpolitz: Hello\nyash: How are you\n"
