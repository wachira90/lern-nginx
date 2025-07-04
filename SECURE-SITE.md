# SECURE SITE NGINX

## http section

```
map $http_user_agent $block_bots {
    default 0;
    "~*GPTBot" 1;
    "~*Amazonbot/0.1" 1;
    "~*ClaudeBot" 1;
    "~*MJ12bot" 1;
    "~*Googlebot" 1;
    "~*curl" 1;
    "~*bingbot" 1;
    "~*Go-http-client" 1;
    "~*Googlebot-Image" 1;
}
map $request_uri $block_env {
    default         0;
    ~*\.env         1;
}
```

## server section

```
if ($block_bots) {
    return 403; # Or 444
}

if ($block_env) {
    return 401;
}
```

