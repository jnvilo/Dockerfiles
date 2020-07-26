This is a very basic centos8 nginx frontend to serve django static files. 

The static files are expected to be mounted in locations defined as follows:

```

      location /static/assets {
                alias /app/assets;
        }

        location /static {
                alias /app/static;
        }

```
