# WP Multi Domains

An alternative to setting up single domains sites on single Wordpress installation without the need of a multi-site network setup.
Each domains shares the same WP Core, contains their own database, and have access to all available plugins and themes within the `wp-content` directory saving file storage space. 

## Usage
Setup is easily done by editing the `wp-config.php` file and including the domains and its database credentials within the `switch` statement. 

```
switch( $domain ) {
    case 'mysite.com':
        define('DB_USER', 'mysite_user');
        define('DB_NAME', 'mysite_database');
        define('DB_HOST', 'localhost');
        define('DB_PASSWORD', 'password');
        break;
    default:
        define('DB_USER', 'default_user');
        define('DB_NAME', 'default_database');
        define('DB_HOST', 'localhost');
        define('DB_PASSWORD', 'password');
        break;
}
```

Each domain can have their own uploads path for images and other static files by defining the 'UPLOADS' path. 

```
switch( domain() ) {
    ...
    case 'mysite.com':
        ...
        define('UPLOADS', 'path/to/upload/directory' );
        break;
    ...
}
```

Before running any WP CLI commands, set the MAIN_DOMAIN to the desired working domain with the following command:
```
wp config set MAIN_DOMAIN <domain>
```
