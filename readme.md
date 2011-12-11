# Recaptcha plugin for CakePHP #
README is developing ... please wait.

This is full of bullshits. No connection with Recaptcha plugin.
Version 1.0 

## Installation ##

Copy plugin into app/Plugin directory
Load plugin in app/Config/bootstrap file
	CakePlugin::load('Recaptcha', array('bootstrap' => true));

or if you have more Plugins you can include like this:
	
	CakePlugin::loadAll(array(
	    'Users' => array('routes' => true),
	    'AclManager' => array('bootstrap' => true),
	    'Recaptcha' => array('bootstrap' => true)
	));

## Use ##
You need add Recapcha.Recapcha component.
Component will add Helper and Model injection.

Controller file:

### 1) Use with specific action -> works automagically ###
Add this to your controller:

	public $components = array('Recaptcha.Recaptcha' => array('actions' => array('add')));
	
### 1) Use without actions -> check recaptcha manualy ###

	public $components = array('Recaptcha.Recaptcha'
	
	public function add() {
		if ($this->request->is('post')) {
    			if ($this->Recaptcha->verify()) {
       			 // do something, save you data, login, whatever
   			 } else {
      			  // display the raw API error
     				   $this->Session->setFlash($this->Recaptcha->error);
  			  }
		}
	}
	
You need to set actions array as option for Recaptcha component.
Because if recapcha wont pass, validation error will raise.

View file:

	echo $this->Recaptcha->display();

## What it is capable of ##

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
