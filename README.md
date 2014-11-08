# redbean4laravel4
### A Laravel 4 package for RedBeanPHP ORM 4.1

This is a Laravel 4 package to allow the use of [Redbean PHP ORM](http://redbeanphp.com).

### How to use

Add 
	
	"mamift/redbean4-laravel4":"dev-master" 
	
to your composer.json file. Then add

	'Mamift\Redbean4Laravel4\Redbean4Laravel4ServiceProvider'

to your Laravel service provider's array in app.php inside the config/ folder.

Because RedBeanPHP also includes it's own facade class as "R", there is no need to add anything into the alias array.

### A note on its implementation

Because the author of RedBeanPHP has not made RedBean completely compatible with Composer (due to the they use PHP namespaces), the rb.php file (that RedBeanPHP is most commonly distributed in) does not appear to be autoloadable by composer (and thus not usable in Laravel like other packages). 

What this package does is load rb.php for each PHP request; under the "autoload" JSON object inside composer.json, it is specified as part of the "files" array:

	{
	    "autoload": {
    	    "files": [
    	        "src/Mamift/Redbean4Laravel4/rb.php"
    	    ]
    	}
	}
	
A quote from the [Composer documentation](https://getcomposer.org/doc/04-schema.md#files) says:
>If you want to require certain files explicitly on every request then you can use the 'files' autoloading mechanism. This is useful if your package includes PHP functions that cannot be autoloaded by PHP.