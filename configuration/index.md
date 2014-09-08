# Configuration

An app has always multiples configurations; for example, the dev configuration is different from the production one. On the dev
configuration your code may need to talk to local API and may have some more debugging stuff. On the other side, the production configuration will allow access to production API.

When creating a tarifa project, the cli will generate the following configurations for each wanted platforms:

* **_default_**
* **_dev_**
* **_stage_**
* **_prod_**

These configurations are just naming conventions, you can add any configurations you need and each configuration allows the build
of an unic app.

## **_default_** configuration

The default configuration is the configuration builded if any configuration is given to the tarifa cli.

## **_dev_** configuration

The developpement configuration, all watch stuff will be filled hier if needed.

## **_stage_** configuration

By default, this configuration is be made uploadable on hockeyapp by tarifa if wanted.

## **_prod_** configuration

By default, this configuration is the production one.
