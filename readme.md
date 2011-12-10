#Recpatcha Plugin for CakePHP#

## Installation ##

### Test php code ###

$this->Auth->fields = array('username' => 'email', 'password' => 'passwd');
$this->Auth->loginAction = array('plugin' => 'users', 'controller' => 'users', 'action' => 'login', 'admin' => false);
$this->Auth->loginRedirect = '/';
$this->Auth->logoutRedirect = '/';
$this->Auth->authError = __('Sorry, but you need to login to access this location.', true);
$this->Auth->loginError = __('Invalid e-mail / password combination.  Please try again', true);
$this->Auth->autoRedirect = false;
$this->Auth->userModel = 'Users.User';
$this->Auth->userScope = array('User.active' => 1);