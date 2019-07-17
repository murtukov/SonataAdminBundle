### `service `
Gets a service from the [service container](https://symfony.com/doc/current/service_container.html). 


<table>
    <tbody>
        <tr>
            <td>Signature</td>
            <td><code><b>service</b>(string <b>$id</b>): object|null</code></td>
        </tr>
        <tr>
            <td>Alias</td>
            <td>ser</td>
        </tr>
        <tr>
            <td>Examples</td>
            <td>
	            <ul>
	            <li><code>@=service('my_service').customMethod()</code></li>
	            <li><code>@=service('App\\Manager\\UserManager').customMethod()</code></li>
	            </ul>
            </td>
        </tr>
    </tbody>
</table>

---

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

---
  
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
