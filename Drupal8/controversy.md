Some controversial issues regarding Drupal 8.

## Module Folder
As per [/modules/READEME.txt](https://api.drupal.org/api/drupal/modules!README.txt/8) in Drupal 8 instance, it's recommended to place modules inside sub-folders in the `/modules` folder.
Both _drush_ and _Drupal Console_ will place the newly installed modules in `/modules/contrib` directory.
Using `/modules/contrib` directory is very conveniant. This way any custom developed modules can be placed at `/modules/custom` directory.

_Note that modules in `/sites/all/modules` take precedence over modules in `/modules` folder._ 

## Drush or Drupal Console
_Drupal Console_ is under heavy development with ambitious road map. This means that if there is a task you can do it using _Drupal Console_ now, this can change in matter of weeks or months.

For now, _drush_ main advantage is that it can work with Drupal 6, 7 and 8. So you can only use _drush_ with older Drupal sites. Also existing scripts 

For developing new commands it's recommended to use _Drupal Console_ because it's entirely based on Symfony Console with access to the _Debendency Injection Container_. It has also Symfony components commands like debugging services and routes.
_Drupal Console_ is also greate for creating boilerplate code which can jumbstart Drupal 8 development process.

Pantheon has [greate introductory article on Drush and Drupal Console](https://pantheon.io/introduction-drush-and-drupal-console)

## Route names in routing.yml
As per [Drupal.org Structure of routes page](https://www.drupal.org/node/2092643) the route name is a machine name, so it can take any formate. To keep things clean and clear it's recommended to user the formate *module_name.route_name*. This way we can avoid route name conflicts.

## Controller Class Inheritance
__Should controller class always extends base controller?__

As per [ControllerBase Class documentation](https://api.drupal.org/api/drupal/core!lib!Drupal!Core!Controller!ControllerBase.php/class/ControllerBase/8), the only advantage this class provides is means to access frequently used services from the service container.  
This makes it difficult write unite tests for the controller class. Which means that the controller class should have only _glue code_ that doesn't need much testing. And all heavy business logic should be wrapped in an external service.

