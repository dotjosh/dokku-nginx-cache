# dokku-nginx-cache

Wire in nginx's proxy cache directives.

### Install

```
dokku plugin:install https://github.com/Aluxian/dokku-nginx-cache.git nginx-cache
```

### Quick start

Enable nginx request caching

```
$ dokku nginx:cache:enable myapp
```

Disable nginx request caching

```
$ dokku nginx:cache:disable myapp
```

### Configuration

Currently there are no configuration options. However, Nginx does obey a number of caching- and `X-Accel-*`-related headers.

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
