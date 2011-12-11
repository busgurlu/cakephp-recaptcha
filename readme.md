# Recaptcha plugin for CakePHP #
README is developing ... please wait.

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

### Controller file: ###

#### 1) Use with specific action -> works automagically ####
Add this to your controller:

	public $components = array('Recaptcha.Recaptcha' => array('actions' => array('add')));
	
Component add Recaptcha helper to yout controller automaticaly.
Component add to your Model validation of recaptcha, if recaptcha is worong it set error message to recaptcha field in your Model.

#### 2) Use without actions -> check recaptcha manualy ####
Component add Recaptcha helper to your controller automaticaly.

	public $components = array('Recaptcha.Recaptcha');
	
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
	

### View file: ###
	echo $this->Form->create($model);
	echo $this->Form->input('username;
	echo $this->Form->input('email');
	echo $this->Recaptcha->display();
	echo $this->Form->submit();
	echo $this->Form->end();

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
