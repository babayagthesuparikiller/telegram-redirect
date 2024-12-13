import com.sun.net.httpserver.HttpServer;
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpExchange;

import java.io.IOException;
import java.net.InetSocketAddress;

public class RedirectServer {
    public static void main(String[] args) throws IOException {
        // Create the HTTP server on port 8080
        HttpServer server = HttpServer.create(new InetSocketAddress(8080), 0);
        
        // Set up the handler for the root URL
        server.createContext("/", new RedirectHandler());
        
        // Start the server
        server.setExecutor(null);
        System.out.println("Server started on http://localhost:8080/");
        server.start();
    }

    static class RedirectHandler implements HttpHandler {
        @Override
        public void handle(HttpExchange exchange) throws IOException {
            // Define the target redirect URL
            String redirectUrl = "https://t.me/+jgQ9MZOOk29mNGRl";

            // Set the res
