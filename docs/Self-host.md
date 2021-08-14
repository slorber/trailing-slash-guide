# Self-hosted HTTP servers

We will serve the [static](../static) folder using different HTTP servers.

## Apache

### Default settings

The Apache server has the following configuration in `sites-available`:

```apache
<VirtualHost *:80>
	ServerName trailing-slash-guide-apache-default.sida-chen.com
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/html/static
	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

**Deployment**: [trailing-slash-guide-apache-default.sida-chen.com](http://trailing-slash-guide-apache-default.sida-chen.com)

| Url                | Result      |
| ------------------ | ----------- |
| /file              | 💢 404      |
| /file/             | 💢 404      |
| /file.html         | ✅          |
| /folder            | ➡️ /folder/  |
| /folder/           | ✅          |
| /folder/index.html | ✅          |
| /both              | ➡️ /both/    |
| /both/             | ✅          |
| /both.html         | ✅          |
| /both/index.html   | ✅          |

### How do I...

- ...make the `/file` path accessible?
  A: Add the following to your configuration:
  ```apache
	RewriteEngine On
	RewriteCond %{REQUEST_URI} !(\.[A-Za-z0-9]*$|/$)
	RewriteRule ^(.*)$ $1.html
  ```
  This appends the `.html` extension to any requests to routes without trailing slash or extension. Check out [trailing-slash-guide-apache-no-extension.sida-chen.com](http://trailing-slash-guide-apache-no-extension.sida-chen.com) for this configuration in action.
  | Url                | Result      |
  | ------------------ | ----------- |
  | /file              | ✅          |
  | /file/             | 💢 404      |
  | /file.html         | ✅          |
  | /folder            | ➡️ /folder/  |
  | /folder/           | ✅          |
  | /folder/index.html | ✅          |
  | /both              | ➡️ /both/    |
  | /both/             | ✅          |
  | /both.html         | ✅          |
  | /both/index.html   | ✅          |
- ...enforce a trailing slash policy?
  A: <!-- TODO -->
- ...make all routes accessible?
  A: <!-- TODO -->

## Nginx

<!-- TODO -->

## Vercel/serve

This is a simple HTTP server run in Node.js. It has the same configuration options and implementation as [Vercel](./Hosting-Providers.md#Vercel), so read more about it there.
