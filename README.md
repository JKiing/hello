# symfony SC7 correction:

## __________     PHP   _________________

### 1) Consider the following class:
```php
class Point
{
public function
_construct (??? $x, ??? $y)
{
}
// ...
}
```
#### Which of the following does ??? replace in order to be able to pass not null numeric values like 3, 7.5, -2 and
* -3.14 to the constructor arguments?
**=> int|float**
* numeric |negative
* decimal
* ?numeric

### 2) A class extends another one and uses a trait. The methods of the trait override the methods with the same name inherited from the parent class.
* **=>  True**
* False

### 3) Which of the following is not a built-in PHP error constant?
 
* E_WARNING
* E_ERROR
* E_NOTICE
*  **=>  E_SYNTAX**
* E_USER_DEPRECATED

### 4) Consider the following function definition:
```php
function sum(int $a, int $b): int
{
    return $a + $b;
｝
```
#### When using PHP 8 or higher, can you call this function as follows without triggering any exception? 
```php
echo sum(a: 3, b: 7);
```
* True
* **=> False**

### 5) Which of the following statements allows to store a temporary message in the session in order to display it after a redirect?
* $session->getFlashes ()->set( 'notice', 'Item added successfully');
* **=> $session->getFlashBag()->add ('notice', 'Item added successfully');**
* $session->flashes()->store('notice', 'Item added successfully');
* $session->flashes->set( 'notice', 'Item added successfully');
* $session->addFlash( 'notice', 'Item added successfully');

### 6) In a controller extending Symfony's AbstractController and with the Request object injected in its action method,, how can you get the value of a variable of type string named foo that was submitted as an HTTP POST parameter?
* $foo = $request->post ('foo');
* $foo = $request->getPost ()->get ('foo');
* $foo = $request->parameters ('POST' )->get ( 'foo');
* **=> $foo = $request->request->get ('foo');**
* $foo = $request->getParameterBag ('POST' )->get ( 'foo');

### 7) What's the recommended naming convention for action methods in Symfony controllers?
* [actionNamelAction() (e.g. showAction())
* do [actionName] () (e.g. doShow() )
* **=> actionName () (e.g. show())**
* perform [actionNamel () (e.g. performShow() )

### 08)Consider the following JSON HTTP request made by a client to the web server:
```
POST /api/order HTTP/1.1
Host: www.thegeekshop.tld
Content-Type: application/json
Content-Length: 83
｛
"reference": "SLT-1337-42",
"amount": "120.00",
"owner": "jane.doe"
}
```
#### Which statement would you use to extract the JSON code from the request?
* $json = $request->body;
* $json = (string) $request;
* $json = $request->toString();
* **=> $json = $request->getContent();**
* $json = json_encode($request->toArray ());

### 9)Consider the following controller in a default Symfony application with both autowiring and autoconfiguration enabled:
```php
use Psr\Log\LoggerInterface;
use Symfony\Component\DependencyInjection\Attribute\Autowire;
use Symfony\Component\HttpFoundation\Response;
class SomeController extends AbstractController {
public function index(#[Autowire(service: 'app.request_logger')] LoggerInterface slogger, ): Response
{
   //
}
```
#### If app.request_logger is a valid service whose class implements LoggerInterface, which will be the service injected into the $logger controller argument?
* The default Symfony logger (the #[Autowire] attribute does not exist)
* The default Symfony logger (the #[Autowire] attribute only works for services, not controllers)
* **=>The default Symfony logger (because you should pass the full logger class path to # [Autowire] instead of the service ID)**
* The service with ID app.request_logger

### 10) Which of the following conditions must controllers meet in a default Symfony application to get the Request object injected when you type-hint a controller action argument with Symfony\Component\HttpFoundation\Request?
* Controllers must be services
* **=> Controllers must extend the base AbstractController.**
* Controllers must be tagged with the controller.service_arguments tag.
* Controllers must be associated to some route (that will trigger the RequestValueResolver).
* None, but the _defaults autowire option must be true in config/services.yaml
 

### 11) Which of the following is not a Symfony's internal built-in parameter that can be retrieved from the Request's attributes bag?
* _locale => cant be retrieve from ($request -> getLocale)
* _route
* _controller
* _route_params
* **=> _action: _action is not a standard built-in parameter in Symfony. If you need specific information about the controller action, you might need to extract it from the _controller parameter**


### 12) Consider the following routes definition:
```yaml
# config/routes. yaml
```
```yaml
blogl:
    path: /blog/{page}
    controller: 'App\Controller\BlogController:: index'
    defaults: { page: 1 }
blog2:
    path: /blog/{slug}
    controller: 'App\Controller\BlogController: :post'
```
### Which route will the /blog/home URL match?
* blog1, because the URL matches both routes and blog1 has preference for being defined first.
* **=> blog2, because the URL matches both routes and blog2 has preference for being the last defined route.**
* blog1, and the value of {page} placeholder will be 1.
* blog2, because {page} placeholder expects an integer and {slug} can match any value.

### 13) Consider the following controller:
```php # src/Controller/UserController.php 
<?php namespace App\Controller;

use Symfony \Component \HttpFoundation \Response; use Symfony\Component \Routing\Attribute\Route;
    #[Route('/users' )]
class UserController｛
        #[Route('', name: 'user_list', methods: ['GET'])]
       public function list(): Response
       {
        // ...
       }
}
```
#### Which of the following statements is true about this route definition when a client requests the /users URL?
* The response will be not found.
* **=> The list() method will be executed.**
* The method must be named index () instead of list()
* The #[Route] attribute must not have an empty URL pattern.

### 14- Which of the following Twig functions generate URLs based on the router mapping configuration?
* href ()=> !Exist
* link()=> !exist
* url_for() => !exist
* **=>path () This Twig function is used to generate URLs based on the router mapping configuration. It generates relative paths**
* url() => This Twig function is similar to path(), but it generates absolute URLs instead of relative paths

### 15) it recommended to add protocol (https://) and/or host (example. com) parts in the path attribute of application routes? 
For example:
```yaml # config/routes. yaml  
blog_post:
    #...
    path: https:// example.com/blog/{slug}.html
```
* Yes. It's a best-practice that makes applications more portable.
* **=> No. Host and protocol will be automatically added by Symfony when needed.**
  
### 16)  Consider the following route definition:
```yaml # config/ routes.yaml
job_positions:
    path: /job-positions-at-???
    controller: 'App\Controller\JobController:: showPositions'
```
#### If the application defines the selected_city parameter in the container with the paris value, which statement does ??? replace in order to generate the /job-positions-at-paris URL?
* %selected_city%
* {{ selected_city }}
* %{selected_city}%
* **=> {selected_city}**
* You cannot use container parameters in the route definition
  
### 17) Consider the following route definition:
```yaml
# config/ routes.yaml
static_page:
  path: /page/{slug}
  controller: 'Symfony\Bundle\FrameworkBundle\Controller\TemplateController'
  defaults: { template: 'static/page.html.twig', private: true }
```
#### Which of these statements is true for this route definition?
* This route will raise an exception because static pages cannot include variables in their paths.
* **=>The response generated by this route will be stored in a public cache.**
* The page.html. twig template can access the route variable with {{ app.request.get('slug') }}.
* The page.html. twig template can only contain HTML contents and no Twig code because this must be a static page.


### 18) Can bundles (both your own bundles and third-party bundles) define compiler passes that are run in your application when installing and enabling those bundles?
* No, for security reasons, only your own application cap define compiler passes.
* No, third-party bundles can't define compiler passes (for security reasons). Your own bundles can.
* No, bundles can't technically define compiler passes.
* **=>Yes.**

### 19)If the name of a parameter in a default Symfony application is **app.email.defaultsender**, would a call to.
```php
$container->getParameter ('app.EMAL.defaultsender') return that parameter?
```
* True
* **=>False**

### 20) Consider the following services configuration:
```yaml # config/services.yaml
imports:
- { resource: ' /parameters.yaml', ignore_errors: true }
```
#### What will happen if the parameters. yaml file exists in the same config/ directory from where it's being imported but contains syntax errors?
* **=>You'll get an exception.**
* The application will return a 404 (not found) HTTP response.
* The application will keep working (and that file won't be imported).

### 21)- Consider the following service definition in a default Symfony application:
```php
//...
class CommandBus
{
    public function _construct
    #[??? ([
        SomeService:: class, AnotherService:: class,
        private ContainerInterface $locator,
    ]) ]
    //
｝
```
#### If both SomeService and AnotherService exist in the application, which attribute does ??? successfully replace in order to inject a service locator argument in this service constructor?
* **=> AutowireLocator**
* AutowireServiceLocator
* AutowireCallable
* AutowireServiceClosure
* Autowire

### 22) A default Symfony application defines the following environment variable in the . env file:
```yaml
#. env
MONGODB_URL="mongodb: //db_user:db_password@127.0.0.1:27017/db_name"
```
#### Which would be the actual value of a configuration parameter whose value is the **%env(key:user: ur l:MONGODB_URL)%** expression?
* key
* user
* **=> MONGODB_URL**
* db_user

### 23) In a default Symfony application, there's the following service configuration:
```yaml
# config/services.yaml
services:
# ...
App\:
    resource: '../src/'
```
#### Which attribute would you apply to a PHP class defined under the App\ namespace and which shouldn't be registered as a service?
* #[Autowiring(false)]
* **=> #[Exclude]**
* #[Target]
* #[IsExcluded]
* #[Autowire(false)]

-------------// twig // --------
### 24) Which will be the result of executing this Twig snippet?
```twig
 {{ block("footer", "base.html.twig") }}
```
* It renders the contents of the footer block (the second argument base.html. twig is ignored).
* It renders the contents of the footer block. If that block is undefined, it renders the contents of the base.html. twig template as a fallback content.
* This code throws an exception because block() doesn't accept more than 1 argument.
* **=> It renders the contents of the footer block from the **base.html.twig** template.**

#### 25) Which of the following statements can you use to print the contents of a Twig template variable called article in the Symfony prod environment?
* **=> {{ dump (article) }}**
* {{ debug(article) }}
* {{ var_export(article) by
* {{ debug_zval_dump(article) }}
* None of the above.

#### 26)Consider the following Twig snippet:
```twig
{% for i in (1..10) | reverse|batch (3, 1) %}
  {% for j in i %}
   {{j}}
  {% endfor %}
{% endfor %}
```
#### What will be the output when rendering this template?
* 123
* 10 9 8
* 1234567891011
* **=> 109 87 6 54 321 11**
* This code will raise an exception

#### 27) A Symfony application wants to store the templates in the resources/views/ directory instead of the default templates/ directory. Which statements do XXX and YYY successfully replace in the following config to achieve that?
```yaml
# config/packages/twig.yaml
twig:
    XXX: ['YYY']
```
* path and '@resources/views/'
* templates and 'kernel.root_dir%/resources/views/'
* path and '@Framework/views/'
* **=> paths and 'kernel.project_dir%/resources/views/'**

#### 28) A default Symfony application defines the following asset configuration:
```yaml
# config/packages/framework.yaml
framework:
    assets:
      version: 'v2'
      version_format: '%%s?version=%%s'
      packages:
         docs:
            base_path: /docs/pdf
```
#### A Twig template has the following code:
```twig
   {{ asset ('terms_and_conditions.pdf', 'docs') }} 
```
#### What will be the link generated by the above Twig snippet?
* /docs/pdf/v2/terms_and_conditions.pdf
* **=>/docs/pdf/terms_and_conditions.pdf?version=v2**
* /v2/docs/pdf/terms_and_conditions.pdf
* /docs/pdf/terms_and_conditions.pdf
* terms_and_conditions.pdf?version=v2

### 29) Consider the following Twig snippet:
```twig
{% set result=0 %}
{% for i in 1..5 %}
    {% set result = result + loop. index0 %}
{% endfor %}
The result is: {{ result }}
```
#### What will be the output when rendering this template with the strict_variables configuration option set to true?
* The result is: null
* The result is: 0
* **=>The result is: 10**
* The result is: 15
* This code will raise an exception (Variable 'result' does not exist in at line ...)

### 30) Which one of these Twig tags and functions would you most likely use to execute some controller action?
* {{ include() }}
* {{ execute() }}
* {{ action () }}
* {% extends %}
* **=> {{ render() }}**

### 31) A social network application allows users to inform if they will attend some event. The possible answers are Yes, No and Maybe and they are represented with three radio buttons.
#### Which of the following Symfony Validator constraints would you apply on the **$isAttending** property which stores the user's answer?
* #[Assert\Boolean( [true: "yes", false: "no", null: "maybe"])]
* #[Assert\Equal(values: ["yes", "no", "maybe"] )]
* #[Assert\Callback("isAttending" )]
* #[Assert\Oneof ("yes","no", "maybe"] )]
* **=> #[Assert\Choice(["yes","no", "maybe"] )]**

### 32) Consider the following model classes:
```php

use Symfony\Component\Validator\Constraints as Assert;
class Address
{
    #[Assert\NotBlank(groups: ['optional'])]
    protected $street;
    #[Assert\Length (max:5, groups: ['mandatory' ])]
    protected $zipCode;
}

class Author {
    #[Assert\NotBlank]
    protected $name;
    #[Assert\ Valid]
    protected $address;
｝
```
##### When validating the Author class, without specifying any validation group, which properties will be validated?
* All of them (name from Author and zipCode and street from Address).
* name from Author and zipCode from Address.
* Just name from Author (none from Address).
* **=> name from Author and street from Address.**
* Just zipCode from Address.

### 33) Consider the following code:
```php
# src/Model/User. php
namespace App\Model;
use Symfony\Component\Validator\Constraints as Assert;
class User
{
    ???
    public int $age;
}
```
#### Which Symfony Validator constraint does ??? successfully replace to ensure the user is over 18 years old?
* #[Assert\Regex("/^\d+/")]
* #[Assert\Date(before: 'now - 18 years' )]
* **=> #[Assert\Range(min: 18)]**
* #[Assert\Range(min: 17)]
* #[Assert\Birthday(18)]



### 34) Consider the following model class:
```php
namespace App\Model;
use Symfony\Component\Validator\Constraints as Assert;
use Symfony\Component\Validator\Context\ExecutionContextInterface;
class PokerPlayer
{
      ???
      public function checkParticipationEligibility(ExecutionContextInterface $context): void
      {
        //perform validation logic
      }
}
```
#### Which of the following constraints is the most appropriate instead of ??? in order to determine whether or not the player is allowed to play poker?
* #[Assert\Bool(mustBe: true)]
* #[Assert\IsTrue]
* #[Assert\Method]
* **=> #[Assert\Callback]**
* It's not possible to execute the checkParticipationEligibility() method.

### 35) Consider the following form snippet:
```php
use Symfony\Component\Form\FormBuilderInterface;
public function buildForm (FormBuilderInterface $builder, array $options): void {

｝
$builder->add( 'title', null, ['???' => 'custom_name']);
```
#### If the name of the form is product, which option name does ??? successfully replace in order to use a fragment called _product_custom_name_widget to render the widget of that field?
* name
* widget_name
* title_widget_name
* **=> block_name**
* title_name

### 36) Before uploading a huge PDF file using a Symfony form, you compress it as a ZIP file to half its size. However, the application displays an error message, and the file isn't uploaded. Using the very same form you can upload the original PDF file correctly.
#### Which of the following error messages was most likely displayed the first time?
* uploadFormSizeErrorMessage
* zipErrorMessage 
* **=> uploadIniSizeErrorMessage**
* mimeTypesMessage
* pdfErrorMessage

### 37)  Consider the following snippet of a form theme:
```twig
{% block form_row %}
{% set row_attr = row_attr|merge ({class: ???. class|default('') ~ 'some_custom_class'}) %}
      {{ parent() }}
{% endblock %}
```
#### Which statement does ??? successfully replace in order to add a CSS class to the form_row block?
* **=> row_attr**
* parent_attr
* attributes
* _attr
* widget_attr

### 38) Consider the following Twig template code:
```twig
{{ form_start (form) }}
{{ form_row(form. field1) }}
{{ form_row( form.field2) }}
<button type="submit"> submit </button>
{{ form_end (form) }}
```
#### The form has only two fields and the CSRF protection is disabled. What is the effect of the form_end () function in this case?
* **=> It will render nothing except the closing </form> tag.**
* It will render one hidden and empty field related to the CSRF protection.
* It will render the submit button and the closing </form> tag (therefore, this form will display two submit buttons).
* It will render form errors (if any).

  
///   ---------------------------------------HTTP -----------------------------------

### 39) Which of the following is not a built-in form field type class provided by the Symfony Form component?
* LocaleType
* CurrencyType
* LanguageType
* **=> Float Type**
* CountryType

### 40) 302 is one of the server error HTTP status codes.
* True
* **=> False**

### 41) Which of the following messages is mostly associated with the 301 HTTP status code?
* Multiple Choices
* **=> Moved Permanently**
* Found
* Not Modified
* Use Proxy

### 42) Consider the following configuration snippet:
```yaml
# config/packages/framework.-yaml
framework:
  #…..
  ???: '192.0.0.1'
```
#### Which statement does ??? successfully replace in order to avoid issues with HTTP header spoofing when the Symfony application is behind a proxy with the 192.5.0.1 IP address?
* trusted_ips (!Exists)
* proxy_ips (!Exists)
* forwarded (!exists)
* trusted_headers (Exists)
* **=> trusted_proxies**
  
### 43) Which of the following HTTP status codes is mostly associated with the Unauthorized message?
* 400 "bad request"
* **=> 401 => Unauthorized**
* 402: "Payment Required" 

### 44) Consider the following HTTP response headers sent by a Symfony application:
``` НТТР/1.1 200 0K
Set-Cookie: id=Rg3vHJZnehYLjVg7qi3bZjzg; Expires=Sat, 15-Jan-2024 21:47:38 GMT;
Path=/; Domain=. example. com; HttpOnly
Set-Cookie: conn=1295214458; Path=/; Domain=. example. com
Set-Cookie: status=deleted; Expires=Thu, 01-Jan-1970 00:00:01 GMT;
Path=/; Domain=.example.com; HttpOnly
...
```
### Which of those cookies could be manipulated by some JavaScript code executed in the browser?
* **=> conn**
* None of them.
* id and status
* status
* id and conn

### 45) Consider the following controller code:
```php
# src/Controller/DateController.php
namespace App\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\HttpKernel\Attribute\Cache;
use Symfony \Component \Routing\Attribute \Route;

class DateController extends AbstractController {
#[Route('/time')]
#[Cache (maxage: 3600) ] 
public function time(): Response
{
  return $this->render ('date/time.html. twig', ['date' => new \DateTime(),]);
}
```
#### The template just displays the date passed from the controller. A user accesses the /time page twice using the same web browser:
* 1- date/time of the first request: Wed, March 2nd 16:00:00.
* 2- date/time of the second request: Wed, March 2nd 16:50:00.
  
#### Which date/time will the page display on the second request?
* **=> Wed, March 2nd 16:00:00**
* Wed, March 2nd 16:50:00
* It depends on the user's timezone.
* The date when the page was requested by any other user.

### 46) Consider the following snippet of a Twig template:
```twig
{{ render_esi(controller('App| (Controller\ \DefaultController: :news')) }}
```
#### What will be the result of executing this template if ESI caching isn't enabled in the application?
* Symfony will ignore this tag and its contents won't be included in the response.
* **=> This code will be parsed as a regular render() function. No error or exception will be shown.**
* The application will return a 404 error page.
* The application will return a 500 error page.

### 47) Consider the following controller code:
```php
# src/Controller/PageController.php
namespace App\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\Response;

class PageController extends AbstractController
{
  public function termsOfUse): Response {
      $response = $this->render ( 'page/tos.html.twig');
      $response->setLastModified(new \DateTime('2023-06-08 10:00:00'));
    return Sresponse;
}
```
#### Is this response cacheable either on the client (web browser) or on a shared reverse proxy cache like Varnish?
* true
* **=> false**

### 48) Which of the following marks the response as stale, preventing the return of its cached contents?
* $response->staled();
* **=> response->expire();**
* response->cached (false);
* $response->invalidate();
* $response->setNotModified ();

### 49) Which statement does ??? successfully replace to make the following command work as expected when running it as php bin/console app: some-command in the console terminal?
```php
<?php
namespace App\Command;
use Symfony\Component\Console\Attribute\AsCommand;
use Symfony\Component\Console\Command\Command;
use Symfony\Component\Console\Input\InputInterface;
use Symfony\Component\Console\Output\OutputInterface;
#[AsCommand (name: 'app: some-command ' ) ] class SomeCommand extends Command
｛
  protected function execute(InputInterface $input, Output Interface $output): int
  $output->writeln ('Hello world');
  ???
}
```
* You must replace it by return; Otherwise, the command won't work.
* You must replace it by return 0; Otherwise, the command won't work.
* **=> You don't need to replace ??? by anything to make the command work.**

### 50)  Consider the code of the following Symfony Console command:
```php
//1..
use Symfony\Component\Console\Command\Command;
use Symfony \Component\Console\Input\InputInterface; 
use Symfony\Component\Console\Output\OutputInterface;
class GreetCommand extends Command
  public function XXX(private YYY $logger) {
    parent::construct();
  ｝
// ...
}
```
#### Which statements do XXX and YYY successfully replace in order to store Symfony's default logger service in the $logger property?
* __construct() and Symfony\Bridge\Monolog\AbstractLogger
* initialize() and Symfony\Bridge\Monolog\AbstractLogger
* initialize() and Symfony\Component\Logger\AbstractLogger
* **=> __construct() and Psr\Log\LoggerInterface**
* initialize() and Psr\Log\LoggerInterface

### 51) Which of the following are built-in methods of the Output Interface interface? (multi reponses)
* **=> isDebug ()**
* isMuted ()
* isSilent()
* **=> isQuiet()**
* **=> isVeryVerbose()**

### 52) Identify the correct list of words to complete the following sentence:
The bin/console CLI script creates an instance of .......... and calls its run method. The latter can take a/an ........... object as its first argument and a/an .......... as its second argument.
* Kernel / Request / Response
* Application / Request / Response
* **=> Application / Input / Output**
* CliApplication / StdIn / StdOut
* Kernel / Input / Output

### 53) Which of the following malicious attacks allows a hacker to exploit the client's authentication trust to make them execute undesired critical actions?
* Cross Site Scripting (XSS)
* Denial of Service (DoS)
* **=> Cross Site Request Forgery (CSRF)**
* SQL injection

### 54) A Symfony application wants to store in the database the last login date of users when they successfully log in into the application. Which security event would you listen to?
* **=> Symfony\\Component\\Security\\Http\\Event\\LoginSuccessEvent**
* Symfony\\Component\\Security\\Core\\Event\\AuthenticationSuccessEvent
* Symfony\\Component\\Security\\Http\\Event\\AuthenticationTokenCreatedEvent
* Symfony\\Component\\Security\\Http\\Event\\CheckPassportEvent

### 55) Consider the following application security configuration:
```yaml
# config/packages/security.yaml
security:
  AAA:
    secured_area:
      pattern: ^/
    http_basic:
      realm: "Secured Demo Area"
  BBB:
    - { path: "^/admin', roles: 'ROLE_ADMIN' }
  ССС:
    users_in_memory:
    memory:
      users:
        ryan: { password: 'ryanpass', roles: 'ROLE_USER' }
        admin: { password: 'kitten', roles: 'ROLE_ADMIN' }
  DDD:
    Symfony\Component\Security\Core\User\PasswordAuthenticatedUserInterface: 'auto'
```
#### Which of the following keywords do AAA, BBB, CCC, and DDD keys successfully replace in order to secure the application?
* password_hashers / access_control / firewalls / providers
* access_control / providers / password_hashers / firewalls
* **=> firewalls / access_control / providers / password_hashers**
* providers / firewalls / password_hashers / access_control
* firewalls / password_hashers / providers / access_control

### 56) The passport returned by security authenticators contain the object of the user that will be authenticated.
* **=> True**
* False

### 57) In a default Symfony application, "User A" successfully impersonates "User B". Which will be the roles of the logged in user?
* The roles of "User A".
* The roles of "User B".
* The roles of "User B" plus a special security attribute called IS_IMPERSONATOR.
* **=> The roles of "User A" and "User B" combined.**

### 58) What is the recommended file path for the functional test of a controller called UserController in a default Symfony application?
* src/Tests/Functional/UserControllerTest.php
* src/Controller/Tests/UserController. php A
* kernel.tests_dir%/Controllers/UserController.php
* **=> tests/Controller/UserControllerTest.php**
* test/Security/Controller/UserTest. php

### 59) Consider the following test code:
```php
$client = static:: createClient();
$client→>request ('GET', '/');
$this->assertEquals(200, ???, 'The homepage loads correctly');
```
#### Which expression does ??? successfully replace in order to execute this test without any errors?
* $client->getResponse ()->getHttpStatusCode()
* $client->getStatusCode()
* **=> $client>getResponse()->getStatusCode()**
* $client->getRequest（)->getCode()
* $client->getLastCode()

### 60) Consider the following functional test code:
```php
$client = static:: createClient();
$crawler = $client->request ( 'GET', '/');
$data = $crawler->filter('a')->extract('href');
```
#### After executing the following functional test, the $data variable will be an array containing the URLs of all homepage links.
* **=> True**
* False

### 61)Consider the following functional test snippet:
```php
$client1 = static:: createClient();
$client2 = static:: createClient (['environment' => 'prod']);
$clientl->insulate();
$client2->insulate();
```
#### In which environment does each HTTP client run?
* You cannot create two different clients in the same test.
* Both clients will run in the test environment.
* Both clients will run in the prod environment.
* **=> $client 1 will run in the test environment and $client will run in the prod environment.**
* None of the above answers is correct.

### 62) In a default Symfony application, which of the following commands is most likely to execute all unit and functional tests?
* ./run_tests.sh
* php bin/console test:run
* php bin/console test: run --unit --functional
* **=> ./bin/phpunit**

### 63) Which of the following is not a method provided by the Symfony Filesystem component?
* readlink
* exists
* rename
* **=> tempnam**
* permission

### 64) Which kind of callback can you register as a listener when using the EventDispatcher component?
* A function name as a string.
* An array containing an instance and the method name to invoke on it.
* A \Closure instance.
* Any object that implements the _invoke () method.
* **=> All of the above are correct.**

### 65) Which of the following templates are valid for customizing 403 error pages in a Symfony web application that has installed and configured Twig?
* templates/TwigBundle/error.403. twig
* templates/Resources/TwigBundle/views/error/403.html.twig
* bundles/TwigBundle/Exception/403.html.twig
* **=> templates/bundles/TwigBundle/Exception/error403.html.twig**
* templates/bundles/TwigBundle/Exception/error.html.twig


### 66) you don't explicitly set the priority of an event listener, the EventDispatcher component considers that the listener has a -2048 priority.
* True
* **=> False**

### 67) Consider the following code snippet related to the Symfony PropertyAccess component:
```php 
$persons = [
    ['first_name' = 'Jane', '...'],
    ['first_name' → 'John', '...'],
    // ...
];
$value = $propertyAccessor->getValue ($persons, ???));
```
#### Which statement does ??? successfully replace to get John as the value of the $value variable?
* **=> '[1][first_namel'**
* '1.first_name'
* 'persons.1. first_name'
* '//first_name: eq (1) '

### 68) Consider the following code snippet that uses Symfony's HttpClient:
```php
use Symfony\Component\HttpClient\HttpClient;
use Symfony \Component \HttpClient\???;
$client = HttpClient:: create();
$client = new ??? ($client, 'https://api\.github\.com/' => [
      'headers' => [
      'Accept' → 'application/vnd.github.v3+json',
      'Authorization' = 'token '.$githubToken,
      ],
]);
```
#### Which statement does ??? successfully replace to add these HTTP headers only when making requests to the GitHub API servers?
* **=> CurlHttpClient**
* HttplugClient
* ScopingHttpClient
* Psr18Client
* CachingHttpClient

### 69) Consider the following code snippet related to the Symfony Mime component:
```php
use Symfony\Component \Mime\MimeTypes;
$guesser = new MimeTypes);
$mimeType = $guesser->guessMimeType('/some/path/to/file.gif');
```
#### If file-gif exists, but it's in fact file.pdf and its extension was changed by mistake by a user, which will be the value of $mimeType?
* ' image/gif'
* **=> application/pdf'**
* null
* ['application/pdf', 'image/gif']
* ['image/gif','application/pdf']

### 70) Which of the following would you use to define the serialization groups applied to a message sent through the Symfony Messenger component?
* **=> SerializerStamp**
* ValidationStamp
* SentStamp
* GroupStamp
* HandledStamp

### 71) In a default Symfony application with the Clock component installed, can you replace any occurrence of DateTime or DateTimeImmutable in your code with the DatePoint class from Clock?
* **=> No, DatePoint is not fully compatible with PHP's DateTimeInterface.**
* Yes, because DatePoint extends DateTimeImmutable.

### 72) A default Symfony application shows a 500 (Internal Server Error) error both in dev and prod environments. Which log file will contain more error lines?
* var/log/dev. log
* Both log files will contain a similar number of lines.
* **=> var/log/prod.log**

### 73)In which of the following files does Symfony recommend defining an environment variable that is only used when running tests on your local development machine?
* .env.local
* **=> .env.test.local**
* .env.test
* .env.dev.local
* .env.dev
  
### 74) Consider the following code snippet related to the Lock component:
```php
$lock = $factory->createLock( 'export-data', 30);
```
#### What does 30 mean in this code?
* If the lock is in use by other processes, acquire() will try to acquire it for up to 30 seconds and will return false otherwise.
* If the lock is in use by other processes, acquire() will be called up to 30 times to try to acquire it.
* **=> If the lock is in use by other processes, Symfony will wait 30 seconds before two consecutive calls to acquire().**
* If the lock is acquired, it will expire (and be released) 30 seconds later.


### 75) Consider the following snippet of a custom Symfony Messenger handler:
```php
namespace App MessageHandler;
use App \Message \SomeMessage;
use Symfony\Component \Messenger\Handler\MessageHandlerInterface;
class SomeMessageHandler implements MessageHandlerInterface
{
  public function ??? {
  }
}
```
#### If this handler is used in a default Symfony application with autoconfiguration enabled, which statement does ??? successfully replace to make this handler process any message of type SomeMessage without adding any configuration?
* handle (SomeMessage $message, StackInterface $stack)
* process (MessageBusInterface $bus, SomeMessage $message)
* handle(StackInterface $stack)
* **=> invoke (SomeMessage $message)**
* invoke ()


