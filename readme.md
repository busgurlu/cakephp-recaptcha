# Recaptcha plugin for CakePHP #

Version 1.0 

## Installation ##
	
	$var array = array();


`this->Auth->fields = array('username' => 'email', 'password' => 'passwd');
$this->Auth->loginAction = array('plugin' => 'users', 'controller' => 'users', 'action' => 'login', 'admin' => false);
$this->Auth->loginRedirect = '/';
$this->Auth->logoutRedirect = '/';
$this->Auth->authError = __('Sorry, but you need to login to access this location.', true);
$this->Auth->loginError = __('Invalid e-mail / password combination.  Please try again', true);
$this->Auth->autoRedirect = false;
$this->Auth->userModel = 'Users.User';
$this->Auth->userScope = array('User.active' => 1);`

## What it is capable of ##

You can use the plugin as it comes if you're happy with it or, more common, extend your app specific user implementation from the plugin.

The plugin itself is already capable of:

* Validate captcha with all cakephp Models

## How to extend the plugin ##

## Requirements ##

* PHP version: PHP 5.2+
* CakePHP version: Cakephp 2.0.x Stable

## Support ##

## License ##

Copyright 2010-2011, [Lamanabie](http://cakephp.siotn.eu)

## Copyright ###

Copyright 2010-2011<br/>

http://cakephp.siotn.eu
