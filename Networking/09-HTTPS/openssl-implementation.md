# 🛠️ OpenSSL Engine Systems Integration Guide

This guide details integrating OpenSSL cryptographic wrappers over standard POSIX socket descriptors in C.

---

## 1. Wrapping Socket Descriptors with SSL Handles

```c
#include <openssl/ssl.h>
#include <openssl/err.h>

// After standard socket accept() returns client_fd...
SSL_CTX *ctx = SSL_CTX_new(TLS_server_method());
SSL *ssl = SSL_new(ctx);
SSL_set_fd(ssl, client_fd);            // Bind OpenSSL handle to socket descriptor

if (SSL_accept(ssl) <= 0) {            // Perform TLS handshake
    ERR_print_errors_fp(stderr);
} else {
    char buf[1024];
    int bytes = SSL_read(ssl, buf, 1023); // Decrypt data automatically
    SSL_write(ssl, "HTTP/1.1 200 OK\r\n\r\n", 19); // Encrypt data automatically
}
```
