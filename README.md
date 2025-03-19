# REFLECTION 

### 1. This Rust function, `handle_connection`, reads and processes an incoming HTTP request from a `TcpStream`. It uses a `BufReader` to efficiently read the stream line by line, collecting the request headers into a `Vec<String>`. The `.take_while(|line| !line.is_empty())` ensures reading stops at the first empty line, marking the end of the headers. Each line is unwrapped from a `Result<String, std::io::Error>` to extract the actual string content. Finally, the collected request is printed in a formatted manner using `println!`. This function essentially logs the HTTP request headers received over the TCP connection.

### 2. <img width="802" alt="Commit2.png" src="https://github.com/user-attachments/assets/db81a075-0dd6-4bd2-ba47-ebe6d507279f" />