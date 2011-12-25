# Recaptcha plugin for CakePHP #

Version 1.0 

## Installation ##

Copy plugin into app/Plugin directory
Add following lines in yout app/Config/bootstrap.php file

	CakePlugin::load('Recaptcha', array('bootstrap' => true));

or if you have more Plugins you can include like this:
	
	CakePlugin::loadAll(array(
	    'Users' => array('routes' => true),
	    'AclManager' => array('bootstrap' => true),
	    'Recaptcha' => array('bootstrap' => true)
	));

Do not call only CakePlugin::loadAll(); beacuse your bootstrap file will be not included and your plugin will not work correctly.

To use the recaptcha plugin its required to modify these two lines in app/Plugins/recaptcha/Config/bootstrap.php file

	Configure::write('Recaptcha.publicKey', 'your-public-api-key');
	Configure::write('Recaptcha.privateKey', 'your-private-api-key');
	
Don't forget to replace the placeholder text with your actual keys!

Keys can be obtained for free from the [Recaptcha website](http://www.google.com/recaptcha)

Controllers that will be using recaptcha require the Recaptcha Component to be included. Through inclusion of the component, the helper is automatically made available to your views.

## Use ##
You need add Recapcha.Recapcha component.
Component will add Helper and Model injection.

### Controller file: ###

#### 1) Use with specific controller action or actions -> works automagically ####
Commponent add field recaptcha and validation to your Model on fly for this action.

Add this to your controller:

	public $components = array('Recaptcha.Recaptcha' => array('actions' => array('add', 'delete')));
	
Add actions where you really use Recaptcha.
Component add to Model validation rules if match current controller->action with array actions.

Add this to your view:
	
	echo $this->Recaptcha->display();

If for some reason you decide not to check the Recaptcha, you can opt-out by calling $this->[MODEL]->recaptcha=true; before you validate/save your data.

	public $components = array('Recaptcha.Recaptcha' => array('actions' => array('add', 'delete')));

	public function add() {
		if ($this->request->is('post')) {
		$this->User->recaptcha=true;
		if ($this->User->save($this->request->data)) {
			//save action
		} else {
			//fail action
		}
	    }
	}

#### 2) Use without actions -> check recaptcha manualy ####

You have to verify captcha manually in your controller.
Add this to your controller:

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
	

### Example of view file: ###
	echo $this->Form->create('User');
	echo $this->Form->input('username');
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

Copyright 2009-2010, Cake Development Corporation

Licensed under The MIT License
Redistributions of files must retain the above copyright notice.

## Copyright ###
Licensed under The MIT License
Redistributions of files must retain the above copyright notice.
Copyright 2010-2011

[My blog](http://cakephp.siotn.eu)
