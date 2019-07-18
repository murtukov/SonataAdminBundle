
Expression language
===================

All definition config entries can use expression language but it must be explicitly triggered using `@=` prefix. This bundle provides a set of registered functions and variables. For more details on expression syntax see the [official documentation](http://symfony.com/doc/current/components/expression_language/syntax.html).

## Contents
- [Registered functions](#registered-functions):
	- [service](#service)
	- [parameter](#parameter)
	- [isTypeOf](#istypeof)
	- [resolver](#resolver)
	- [mutation](#mutation)
	- [arguments](#arguments)
	- [globalId](#globalid)
	- [fromGlobalId](#fromglobalid)
	- [newObject](#newobject)
	- [call](#call)
	- [hasRole](#hasrole)
	- [hasAnyRole](#hasanyrole)
	- [isAnonymous](#isanonymous)
	- [isRememberMe](#isrememberme)
	- [isFullyAuthenticated](#isfullyauthenticated)
	- [isAuthenticated](#isauthenticated)
	- [hasPermission](#haspermission)
	- [hasAnyPermission](#hasanypermission)
	- [getUser](#getuser)
- [Registered variables](#registered-variables)
- [Private services](#private-services)
- [Custom expression functions](#custom-expression-functions)
- Single and double quotes in expressions


## Registered functions

### service
**Signature**: <code><b>service</b>(string <b>$id</b>): object|null</code> &nbsp;**Alias**: `ser`

Gets a service from the [service container](https://symfony.com/doc/current/service_container.html). Private services should be explicitly tagged to be accessible, see [this](#private-services) section for more details.

Examples:
```yaml
@=service('my_service').customMethod()

# Using the 'ser' alias
@=ser('my_service').customMethod()

# Using the FQCN for the service name (only works for public services).
# Note the double quotes.
@=ser("App\\Manager\\UserManager").someMethod()

# If using single quotes, you must use 4 slashes
@=ser('App\\\\Manager\\\\UserManager').someMethod()
```

---

### parameter
**Signature**: <code><b>parameter</b>(string <b>$name</b>): mixed</code> &nbsp;**Alias**: `param`

Gets a parameter from the [service container](https://symfony.com/doc/current/service_container.html). 

Examples:
```yaml
# Example 1.
@=parameter('kernel.debug')

# Example 2: using the 'param' alias
@=param('kernel.debug')
```

---
  
### isTypeOf
**Signature**: <code><b>isTypeOf</b>(string <b>$className</b>): boolean</code>

Checks if `value` is instance of the given class name.

Example:
```yaml
@=isTypeOf('App\\User\\User')
```
---

### resolver
**Signature**: <code><b>resolver</b>(string <b>$alias</b>, array <b> $args</b> = []): mixed</code> &nbsp;**Alias**: `res`

Calls a method on the tagged service `overblog_graphql.resolver` with `$args`

Examples:
```yaml
# Using aliased resolver name
@=resolver('blog_by_id', [value['blogID']])

# Using FQCN::methodName
@=res('App\\GraphQL\\Resolver\\UserResolver::findOne', [args, info, context])
```
---

### mutation
**Signature**: <code><b>mutation</b>(string <b>$alias</b>, array <b> $args</b> = []): mixed</code> &nbsp;**Alias**: `mut`

Calls a method on the tagged service `overblog_graphql.mutation` passing `$args` as arguments.

Examples:
```yaml
# Using aliased mutation name
@=mutation(‘remove_post_from_community’, [value])</code></li>
@=mut(‘remove_post_from_community’, [value])</code></li>
```

---

### arguments
**Signature**: <code><b>arguments</b>(array <b>$mapping</b>, mixed <b> $data</b>): mixed</code>

Transforms and validates a list of arguments. See [Arguments Transformer](https://stackedit.io/annotations/arguments-transformer.md) for more details.

Examples:
```yaml
@=arguments([‘input’ => ‘MyInput’], [‘input’ => [‘field1’ => “value1”]])
@=arguments([‘input’ => ‘MyInput’], [‘input’ => [‘field1’ => “value1”]])
```

---

### globalId
**Signature**: <code><b>globalId</b>(string|int <b>$id</b>, string <b> $typeName</b> = null): string</code>

Relay node globalId.

Examples:
```yaml
@=globalId(15, ‘User’)
@=globalId(15, ‘User’)
```

---

### fromGlobalId
**Signature**: <code><b>fromGlobalId</b>(string <b>$globalId</b>): array</code>

Relay node globalId.

Examples:
```yaml
@=fromGlobalId(‘QmxvZzox’)
@=fromGlobalId(‘QmxvZzox’)
```

---

### newObject
**Signature**:  <code><b>newObject</b>(string <b>$className</b>, array <b> $args</b> = []): object</code>

Creates an instance of an object from given class name, passing `$args` to its constructor.

Examples:
```yaml
@=newObject(‘AppBundle\User\User’, [‘John’, 15])
@=newObject(‘AppBundle\User\User’, [‘John’, 15])
```

---

### call
**Signature**: <code><b>call</b>(mixed <b> $target</b>, array <b> $args</b> = [], bool <b> $static</b> = false): object</code>

Calls the target method, passing `$args` as arguments.

Examples:
```yaml
@=call(service(‘my_service’).method, [“arg1”, 2])
@=call(service(‘my_service’).method, [“arg1”, 2])
```

---

### hasRole
**Signature**: <code><b>hasRole</b>(string <b>$role</b>): bool</code>

Checks whether the logged in user has a certain role.

Examples:
```yaml
@=hasRole(‘ROLE_API’)
@=hasRole(‘ROLE_API’)
```

---

### hasAnyRole
**Signature**: <code><b>hasAnyRole</b>(string <b> $role1</b>, string <b> $role2</b>, …string <b> $roleN</b>): bool</code>

Checks whether the logged in user has any of the given roles.

Examples:
```yaml
@=hasAnyRole(‘ROLE_API’, ‘ROLE_ADMIN’)
@=hasAnyRole(‘ROLE_API’, ‘ROLE_ADMIN’)
```

---

### isAnonymous  
**Signature**: <code><b>isAnonymous</b>(): bool</code>
Checks whether the token is anonymous.


Examples:
```yaml
@=isAnonymous()
```

---

### isRememberMe
**Signature**: <code><b>isRememberMe</b>(): bool</code>

Checks whether the token is remember me.

Examples:
```yaml
@=isRememberMe()
```

---

### isFullyAuthenticated
**Signature**: <code><b>isFullyAuthenticated</b>(): bool</code>

Checks whether the token is fully authenticated.

Examples:
```yaml
@=isFullyAuthenticated()
```

---

### isAuthenticated()  
**Signature**: <code><b>isAuthenticated</b>(): bool</code>

Checks whether the token is not anonymous.

Examples:
```yaml
@=isAuthenticated()
```

---

### hasPermission
**Signature**: <code><b>hasPermission</b>(mixed <b> $var</b>, string <b> $permission</b>): bool</code>

Checks whether the token has the given permission for the given object (requires [symfony/acl-bundle](https://github.com/symfony/acl-bundle) to be installed).

Examples:
```yaml
@=hasPermission(object, ‘OWNER’)
@=hasPermission(object, ‘OWNER’)
```

---

### hasAnyPermission
**Signature**: <code><b>hasAnyPermission</b>(mixed <b> $var</b>, string <b> $permission</b>): bool</code>

Checks whether the token has any of the given permissions for the given object

Examples:
```yaml
@=hasAnyPermission(object, [‘OWNER’, ‘ADMIN’])
@=hasAnyPermission(object, [‘OWNER’, ‘ADMIN’])
```

---

### getUser 
**Signature**: <code><b>getUser</b>(): Symfony\Component\Security\Core\User\UserInterface|null</code>

Returns the user which is currently in the security token storage.

Examples:
```yaml
@=getUser()</code></li>
@=getUser().firstName === 'adam'</code>
```

## Registered variables:

| Variable| Description                                                                                                                                                                                       | Scope                                                                                      |
|:---------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |:------------------------------------------------------------------------------------------ |
| `typeResolver`       | the type resolver                                                                                                                                                                                 | global                                                                                     |
| `object`             | Refers to the value of the field for which access is being requested. For array `object` will be each item of the array. For Relay connection `object` will be the node of each connection edges. | only available for `config.fields.*.access` with query operation or mutation payload type. |
| `value`              | Resolver value                                                                                                                                                                                    | only available in resolve context                                                          |
| `args`               | Resolver args array                                                                                                                                                                               | only available in resolve context                                                          |
| `info`               | Resolver GraphQL\Type\Definition\ResolveInfo Object                                                                                                                                               | only available in resolve context                                                          |
| `context`            | context is defined by your application on the top level of query execution (useful for storing current user, environment details, etc)                                                            | only available in resolve context                                                          |
| `childrenComplexity` | Selection field children complexity                                                                                                                                                               | only available in complexity context                                                       |


Private services
----------------

It is not possible to use private services with `service` or `ser` functions since this is equivalent to call
`get` method on the container. In order to make private services accessible, they must be tagged with `overblog_graphql.global_variable`.

Yaml example:

```yaml
App\MyPrivateService:
    public: false
    tags:
        - { name: overblog_graphql.global_variable, alias: my_private_service }
```

To use a vendor private services:

```php
<?php

$vendorPrivateServiceDef = $container->findDefinition(\Vendor\PrivateService::class);
$vendorPrivateServiceDef->addTag('overblog_graphql.global_variable', ['alias' => 'vendor_private_service']);
```

Usage:

```yaml
MyType:
    type: object
    config:
        fields:
            name:
                type: String!
                resolve: '@=my_private_service.formatName(value)'
```

Custom expression functions
--------------------------

Adding custom expression function is easy since all you need to do is create a tagged service.
Expression functions can help user create simple resolver without having to leave config file,
this also improves performance by removing a useless external resolver call.

Here is an example to add a custom expression equivalent to php `json_decode`:

```php
<?php

namespace App\ExpressionLanguage;

use Overblog\GraphQLBundle\ExpressionLanguage\ExpressionFunction;

class JsonDecode extends ExpressionFunction
{
    public function __construct()
    {
        parent::__construct(
            'json_encode',
            function ($json, $assoc) {
                return sprintf('json_decode(%s, %s)', $json, $assoc);
            }
        );
    }
}
```

now register your service

```yaml
App\ExpressionLanguage\JsonDecode:
    tags: ['overblog_graphql.expression_function']
```

Now `json_decode` can be used in schema:

```yaml
Object:
    type: object
    config:
        fields:
            name:
            type: String!
            resolve: "@=json_decode(value.json_data, true)['name']"
```

**Tips**: At last if this is not an answer to all your needs, the expression language service can be customized
using bundle configuration.
