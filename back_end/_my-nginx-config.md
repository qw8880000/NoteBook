server {                                                                                                                        
    listen          80;
    server_name     www.wangjinle.com wangjinle.com;
    root            /home/ftpuser/HomePage;
    index           index.html;
    error_page 404 = /index.html;

    location /posts/ {
        error_page 404 = http://blog.wangjinle.com;
    }
}

server {
    listen          80;
    server_name     blog.wangjinle.com;
    root            /home/ftpuser/blog/public;
    index           index.html;
    error_page 404 = /index.html;
}

server {
    listen       80;
    server_name  md.wangjinle.com;

    location / {
        proxy_pass http://localhost:3000;
    }
}


server {
    listen       80;
    server_name  jenkins.wangjinle.com;

    location / {
        proxy_pass http://localhost:8080;
    }
}
