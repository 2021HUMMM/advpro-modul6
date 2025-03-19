# REFLECTION 

### 1. Commit 1 Reflection note: 

This Rust function, `handle_connection`, reads and processes an incoming HTTP request from a `TcpStream`. It uses a `BufReader` to efficiently read the stream line by line, collecting the request headers into a `Vec<String>`. The `.take_while(|line| !line.is_empty())` ensures reading stops at the first empty line, marking the end of the headers. Each line is unwrapped from a `Result<String, std::io::Error>` to extract the actual string content. Finally, the collected request is printed in a formatted manner using `println!`. This function essentially logs the HTTP request headers received over the TCP connection.

### 2. Commit 2 Reflection note: 

The updated Rust program introduces an HTTP response mechanism by adding the `fs` module to read an HTML file (`hello.html`) and serve it as a response. Instead of merely printing the HTTP request, it now constructs a proper HTTP response with a `"HTTP/1.1 200 OK"` status line and a `Content-Length` header. The response is formatted using `format!` and sent to the client using `stream.write_all(response.as_bytes()).unwrap();`. This enhancement allows the program to function as a simple web server, serving static HTML content while still preserving its original request-handling logic.

<img width="802" alt="Commit2.png" src="https://github.com/user-attachments/assets/db81a075-0dd6-4bd2-ba47-ebe6d507279f" />

### 3. Commit 3 reflection notes: 

This Rust function, `handle_connection`, processes an incoming HTTP request from a `TcpStream` and sends an appropriate response based on the requested URL. It begins by creating a `BufReader` to read the stream line by line, extracting the first line of the request (`request_line`). If the request matches `"GET / HTTP/1.1"`, it serves `"hello.html"` with an HTTP 200 OK status; otherwise, it serves `"404.html"` with a 404 NOT FOUND status. The function reads the corresponding file’s contents, determines its length, and constructs a proper HTTP response with headers. Finally, the response is written back to the client using `stream.write_all()`. This implementation forms the foundation of a simple web server.

<img width="670" alt="Image" src="https://github.com/user-attachments/assets/fce26118-6123-4d81-b4ee-b22ae8e79d37" >

### 4. Commit 4 reflection note:

This Rust function, `handle_connection`, processes incoming HTTP requests and responds accordingly. It first reads the request line from the `TcpStream` using a `BufReader`. Then, it uses a `match` expression to determine the appropriate HTTP response:
- If the request is `"GET / HTTP/1.1"`, it serves `"hello.html"` with an HTTP 200 OK status.
- If the request is `"GET /sleep HTTP/1.1"`, it introduces a **10-second delay** (`thread::sleep(Duration::from_secs(10))`) before serving `"hello.html"`, simulating a slow response.
- For any other request, it returns a **404 Not Found** response with `"404.html"`.

The function then reads the selected file’s contents, calculates its length, and constructs an HTTP response with headers. Finally, the response is written to the client using `stream.write_all()`. This modification adds a delay for specific requests, making it useful for simulating slow-loading pages or testing concurrency in a multi-threaded server.

