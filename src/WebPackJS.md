- Use `speed-measure-webpack-plugin` to measure building speed
- Do not create an entry for vendors or other stuff that is not the starting point of execution, `optimization.splitChunks` helps you...[ref](https://webpack.js.org/concepts/entry-points/#entrydescription-object)
- Use `compression-webpack-plugin` to compress static files, and we should also set `nginx.conf` like following to open gzip...[ref](https://docs.nginx.com/nginx/admin-guide/web-server/compression/)...[ref](https://webpack.js.org/plugins/compression-webpack-plugin/)
  ```bash
  gzip_static on;
  gzip_proxied any;
  gzip on;
  gzip_min_length 1k;
  gzip_types text/css text/javascript text/xml text/plain text/x-component application/javascript application/json application/xml application/rss+xml font/truetype font/opentype application/vnd.ms-fontobject image/svg+xml;
  gzip_vary on;
  gzip_disable "MSIE [1-6]\.";
  ```
