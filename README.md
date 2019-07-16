# Sonata Admin Bundle

The missing Symfony Admin Generator

[![Latest Stable Version](https://poser.pugx.org/sonata-project/admin-bundle/v/stable)](https://packagist.org/packages/sonata-project/admin-bundle)
[![Latest Unstable Version](https://poser.pugx.org/sonata-project/admin-bundle/v/unstable)](https://packagist.org/packages/sonata-project/admin-bundle)
[![License](https://poser.pugx.org/sonata-project/admin-bundle/license)](https://packagist.org/packages/sonata-project/admin-bundle)

[![Total Downloads](https://poser.pugx.org/sonata-project/admin-bundle/downloads)](https://packagist.org/packages/sonata-project/admin-bundle)
[![Monthly Downloads](https://poser.pugx.org/sonata-project/admin-bundle/d/monthly)](https://packagist.org/packages/sonata-project/admin-bundle)
[![Daily Downloads](https://poser.pugx.org/sonata-project/admin-bundle/d/daily)](https://packagist.org/packages/sonata-project/admin-bundle)

Branch | Travis | Coveralls | Scrutinizer |
------ | ------ | --------- | ----------- |
3.x   | [![Build Status][travis_stable_badge]][travis_stable_link]     | [![Coverage Status][coveralls_stable_badge]][coveralls_stable_link]     | [![Scrutinizer Status][scrutinizer_stable_badge]][scrutinizer_stable_link] |
master | [![Build Status][travis_unstable_badge]][travis_unstable_link] | [![Coverage Status][coveralls_unstable_badge]][coveralls_unstable_link] | [![Scrutinizer Status][scrutinizer_unstable_badge]][scrutinizer_unstable_link] |

## Documentation

Check out the documentation on the [official website](https://sonata-project.org/bundles/admin).

## Support

For general support and questions, please use [StackOverflow](http://stackoverflow.com/questions/tagged/sonata).

If you think you found a bug or you have a feature idea to propose, feel free to open an issue
**after looking** at the [contributing guide](CONTRIBUTING.md).

## License

This package is available under the [MIT license](LICENSE).

[travis_stable_badge]: https://travis-ci.org/sonata-project/SonataAdminBundle.svg?branch=3.x
[travis_stable_link]: https://travis-ci.org/sonata-project/SonataAdminBundle
[travis_unstable_badge]: https://travis-ci.org/sonata-project/SonataAdminBundle.svg?branch=master
[travis_unstable_link]: https://travis-ci.org/sonata-project/SonataAdminBundle

[coveralls_stable_badge]: https://coveralls.io/repos/github/sonata-project/SonataAdminBundle/badge.svg?branch=3.x
[coveralls_stable_link]: https://coveralls.io/github/sonata-project/SonataAdminBundle?branch=3.x
[coveralls_unstable_badge]: https://coveralls.io/repos/github/sonata-project/SonataAdminBundle/badge.svg?branch=master
[coveralls_unstable_link]: https://coveralls.io/github/sonata-project/SonataAdminBundle?branch=master

[scrutinizer_stable_badge]: https://scrutinizer-ci.com/g/sonata-project/SonataAdminBundle/badges/quality-score.png?b=3.x
[scrutinizer_stable_link]: https://scrutinizer-ci.com/g/sonata-project/SonataAdminBundle/?branch=3.x
[scrutinizer_unstable_badge]: https://scrutinizer-ci.com/g/sonata-project/SonataAdminBundle/badges/quality-score.png?b=master
[scrutinizer_unstable_link]: https://scrutinizer-ci.com/g/sonata-project/SonataAdminBundle/?branch=master


### <code>service(string $id): object|null</code>  
&emsp;&emsp;Gets a service from the [service container](#https://symfony.com/doc/current/service_container.html).  
  
&emsp;&emsp;**alias**: `ser`  
&emsp;&emsp;**example**: `@=service('my_service').customMethod()`  
  
### <code>parameter(string $name): mixed</code>  
&emsp;&emsp;Gets a parameter from the [service container](#https://symfony.com/doc/current/service_container.html).  

&emsp;&emsp;**alias**: `param` 
&emsp;&emsp;**example**: `@=parameter('kernel.debug')`  
  
### <code>isTypeOf(string $className): boolean</code>  
&emsp;&emsp;Verifies if `value` is instance of the `$className`  

&emsp;&emsp;**example**: `@=isTypeOf('AppBundle\\User\\User')`

### <code>resolver(string $alias, array $args = []): mixed</code>  
&emsp;&emsp;Calls a method on the tagged service “overblog_graphql.resolver” with `$args`

&emsp;&emsp;**example**: `@=resolver('blog_by_id', [value['blogID']])`
