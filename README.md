### parameter</code>  


Gets a parameter from the [service container](https://symfony.com/doc/current/service_container.html). 

<table>
    <tbody>
        <tr>
            <td>Signature</td>
            <td><code><b>parameter</b>(string <b>$name</b>): mixed</code></td>
        </tr>
        <tr>
            <td>Alias</td>
            <td>param</td>
        </tr>
        <tr>
            <td>Examples</td>
            <td>
	            <ul>
                    <li><code>@=parameter('kernel.debug')</code></li>
                    <li><code>@=parameter('kernel.debug')</code></li>
	            </ul>
            </td>
        </tr>
    </tbody>
</table>


---
  
### <code>isTypeOf(string $className): boolean</code>  
Checks if `value` is instance of the `$className`  

Examples: 
 - `@=isTypeOf('App\\User\\User')`

| Description | Signature |Examples |
|-------------|----------|---------|
|Checks if `value` is instance of the `$className` | code>isTypeOf(string $className): boolean</code> |`@=isTypeOf('App\\User\\User')` |

---

### <code>resolver(string $alias, array $args = []): mixed</code>  
Alias: **res**
Calls a method on the tagged service “overblog_graphql.resolver” with `$args`

Examples: 
 - `@=resolver('blog_by_id', [value['blogID']])`
 - `@=res('blog_by_id', [value['blogID']])`
