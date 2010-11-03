Vendo
===

What is it?
---

A lightweight e-commerce framework developed with the Kohana3 php framework.

It's main goal is to provide an excellent starting base for you to develop e-commerce applications with. It's not designed to be a drop-in e-commerce application, like Magento or OpenCart.

What is special about Vendo?
---

 1. It will be easy to build applications with
 2. The source code will make sense
 3. It will be fast
 4. It will be easy to write extensions for
 5. Development/Support will be as open as possible. Your contributions are welcome and encouraged
 6. It will be fully tested to ensure stability and prevent issue regression

How can I help?
---

 1. Create an issue in this project for your feature/request
 2. Follow the [pull request](http://help.github.com/pull-requests/) procedures

How to install Vendo
---

Vendo has many parts:

 1. vendo-core: the core models and vendo base/exception classes
 2. vendo-acl: ACL classes
 3. vendo-billing: billing/order models and payment gateway classes
 4. vendo-admin: the admin application to manage the database for vendo
 5. vendo-application: a sample e-commerce application

If you just want to demo the whole vendo-application, do:

 1. Check out this repository with the --recursive flag
 2. cd to modules/kostache and run `git submodule init` and `git submodule update`
 3. Install the database:
    * Run the schema.sql file located in application/schema/
    * OR (if you are doing development work, use the migrations)
    * [Liquibase 1.95.](http://www.liquibase.org/download) is used for migrations
    * Install the database connector. [Mysql](http://dev.mysql.com/downloads/connector/j/) is recommended.
    * Run `liquibase --driver=com.mysql.jdbc.Driver --classpath=/path/to/mysql-connector-java-5.1.13-bin.jar --changeLogFile=application/schema/schema.xml --url="jdbc:mysql://<hostname>/<database_name>" --username=<username> --password=<password> migrate`
 4. Make sure the application/photos/ directory is writable by the webserver

If you'd like to use Vendo to develop your e-commerce application, you can omit the vendo-application module, and use the other four (you still need the database). Sometime in the near future, the modules will be broken into their own repositories.

You can use the vendo-application as a starting point, or for inspiration on how to build an application with Vendo.

Using vendo-application as a base
---

You can use the vendo-application module as a base for your e-commerce application. If you are happy with the functionality of the stock controllers but not the views (you should probably never use them as-is), you can replace the view class and templates in your application to get a customized skin on top of it.

Testing
---

One goal of Vendo is to be completely tested. This helps prevent bugs and defines a stable API. We use phpunit for unit tests, and plan on using cucumber for behavior tests once the application ui is stable.

If you contribute code, please make sure that you use TDD or BDD, depending on your contribution.

To run the phpunit tests, simple run `phpunit` from the root of the repository. All tests should pass. Please file an issue if they do not pass on your system.

Integration
---

If you are using the Kohana Template Controller, put this in an extended template controller:

public function after()
{
	$this->template->{{$your_body_variable}} = $this->request->response;

	return parent::after();
}

Then make a templates/layout.mustache file in your application directory with this in it:

{{>body}}

If you take this method, you will need to output the category links, cart link, and the account admin links manually.

This method is untested, so please provide feedback. :)

Tech
---

Here's a list of tech used to build Vendo:

 * [Kohana](http://github.com/kohana/kohana)
 * [KOstache](http://github.com/zombor/KOstache)
 * [Mustache.php](http://github.com/bobthecow/mustache.php)
 * [Auto Modeler](http://github.com/zombor/Auto-Modeler)