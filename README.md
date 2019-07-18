### `service `
**Alias**: `ser`
**Signature**: <code><b>service</b>(string <b>$id</b>): object|null</code>

Gets a service from the [service container](https://symfony.com/doc/current/service_container.html). 

**Examples**:
```yaml
@=service('my_service').customMethod()
# or
@=service('App\\Manager\\UserManager').customMethod()
```

### `parameter`
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

### `isTypeOf`
Checks if `value` is instance of the `$className`  

<table>
    <tbody>
        <tr>
            <td>Signature</td>
            <td><code><b>isTypeOf</b>(string <b>$className</b>): boolean</code></td>
        </tr>
        <tr>
            <td>Examples</td>
            <td>
	            <ul>
	            <li><code>@=isTypeOf('App\\User\\User')</code></li>
	            </ul>
            </td>
        </tr>
    </tbody>
</table>

### `resolver`
Calls a method on the tagged service `overblog_graphql.resolver` with `$args`

<table>
    <tbody>
        <tr>
            <td>Signature</td>
            <td><code><b>resolver</b>(string <b>$alias</b>, array <b> $args</b> = []): mixed</code></td>
        </tr>
        <tr>
            <td>Alias</td>
            <td>res</td>
        </tr>
        <tr>
            <td>Examples</td>
            <td>
	            <ul>
		            <li><code>@=resolver('blog_by_id', [value['blogID']])</code></li>
		            <li><code>@=res('blog_by_id', [value['blogID']])</code></li>
	            </ul>
            </td>
        </tr>
    </tbody>
</table>

### `mutation`
Calls a method on the tagged service `overblog_graphql.mutation` passing `$args` as arguments.

<table>
    <tbody>
        <tr>
            <td>Signature</td>
            <td><code><b>mutation</b>(string <b>$alias</b>, array <b>$args</b> = []): mixed</code></td>
        </tr>
        <tr>
            <td>Alias</td>
            <td><code>mut</code></td>
        </tr>
        <tr>
            <td>Examples</td>
            <td>
	            <ul>
		            <li><code>@=mutation(‘remove_post_from_community’, [value])</code></li>
		            <li><code>@=mut(‘remove_post_from_community’, [value])</code></li>
	            </ul>
            </td>
        </tr>
    </tbody>
</table>

---

|||
|-|-|
| Signature | <code><b>isTypeOf</b>(string <b>$className</b>): boolean</code>|
|Alias|res
| Example | `@=isTypeOf('App\\User\\User')`
