# Broker Server

This repository contains the reference implementation for the Broker as specified in the [Broker Authentication specification](https://apps.wp-api.org/spec/). This is currently running on the primary Broker installation at https://apps.wp-api.org/spec/

## Running your own broker

You can run your own broker for a company app registry, internal use, or development purposes. Simply install this plugin on your site.

The plugin requires the [OAuth Server](https://github.com/WP-API/OAuth1) to be installed and active. Technically speaking, the [REST API plugin](https://github.com/WP-API/WP-API) is not required, but is highly recommended.

Once installed, the broker needs to be registered on the sites it wants to work with, which requires the broker ID and broker verification URL. For your site, the broker ID is the home URL (`home_url()`) and the verification URL is `/broker/verify/` on your site (`home_url( '/broker/verify/' )`). The broker ID can be changed via the `authbroker.id` filter.

To add your broker to the recognised brokers on a site, filter `rest_broker_known_brokers` and add it to the array:

```php
add_filter( 'rest_broker_known_brokers', function ( $brokers ) {
	// 'id' => 'verify URL'
	$brokers['https://example.com/'] = 'https://example.com/broker/verify/';
	return $brokers;
});
```
