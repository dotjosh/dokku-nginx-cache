# Dokku plugin nginx-cache

Easily enable the NGINX cache.

### Install

```
dokku plugin:install https://github.com/koalalorenzo/dokku-nginx-cache.git nginx-cache
```

To validate if it is working you can simply check the `X-Cache-Status`. You can
that easily with `curl` from the command line:

```
$ curl -I http://YOURAMAZINAPP.DOMAIN.EXT/
```

You can validate it by running it multiple times, and after the first time it
will show something like:

```
X-Cache-Status: HIT
```

### Quick start

Enable nginx caching

```
$ dokku nginx-cache:enable MYAPP
```

Disable nginx cache for your app

```
$ dokku nginx-cache:disable MYAPP
```

### Configuration

Currently there are no configuration options. However, Nginx does obey a number of caching- and `X-Accel-*`-related headers.

You can always play around by editing directly the file in `/etc/nginx/conf.d/dokku-cache.conf`

Snippet from [nginx docs][]:

- `X-Accel-Expires`, `Expires`, `Cache-Control`, `Set-Cookie`, and `Vary` set the parameters of response [caching][];
- `X-Accel-Redirect` performs an [internal redirect][] to the specified URI;
- `X-Accel-Limit-Rate` sets the [rate limit][] for transmission of a response to a client;
- `X-Accel-Buffering` enables or disables [buffering][] of a response;
- `X-Accel-Charset` sets the desired [charset][] of a response.

[nginx docs]: http://nginx.org/en/docs/http/ngx_http_proxy_module.html#proxy_ignore_headers
[caching]: http://nginx.org/en/docs/http/ngx_http_proxy_module.html#proxy_cache_valid
[internal redirect]: http://nginx.org/en/docs/http/ngx_http_core_module.html#internal
[rate limit]: http://nginx.org/en/docs/http/ngx_http_core_module.html#limit_rate
[buffering]: http://nginx.org/en/docs/http/ngx_http_proxy_module.html#proxy_buffering
[charset]: http://nginx.org/en/docs/http/ngx_http_charset_module.html#charset
