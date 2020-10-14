# IP Address Fields

This module provides a field for storing an IP address or range.

The shorthand widget allows a user to enter the values in any of the following formats:

```
example.com
10.10.10.10
10.10.10.*
10.10.10.0 - 10.10.12.255
10.10.10.10-20
```

The CIDR widget allows CIDR inputs only:

```
10.10.10.10/32
```

The addresses are stored internally as a long, this allows you to do network computations quickly (e.g. is 10.10.10.10 within the range 10.10.10.0 - 10.10.10.50).

## Example code

This code will find any user entities that have an IP range which includes the visitors current IP address.

```
$visitor_addr = ip2long($user->hostname);
$query = new EntityFieldQuery();
$result = $query
    ->entityCondition('entity_type', 'user')
    ->propertyCondition('status', 1)
    ->fieldCondition('field_yourfieldname', 'start', $visitor_addr, '<=', 0)
    ->fieldCondition('field_yourfieldname', 'end', $visitor_addr, '>=', 0)
    ->execute();
```

## Current Maintainers

- Herb v/d Dool <https://github.com/herbdool/>
- Seeking additional maintainers.

## Credits

- Ported to Backdrop by Herb v/d Dool <https://github.com/herbdool/>
- Originally developed for Drupal by [aidanlis](https://www.drupal.org/u/aidanlis)


## License

This project is GPL v2 software. See the LICENSE.txt file in this directory for
complete text.
