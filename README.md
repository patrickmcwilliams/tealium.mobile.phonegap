PhoneGap Plugin 1.0.1
===============

### Brief ###

This plugin provides the means to tag PhoneGap applications for the purposes of leveraging [Tealium's tag management platform (Tealium IQ)](http://tealium.com/products/enterprise-tag-management/), which permit [Tealium-enabled mobile apps](http://tealium.com/products/enterprise-tag-management/mobile/) to add, remove or edit analytic services remotely, in real-time, without requiring a code rebuild or new release to take effect.

### Table of Contents ###

- [Requirements](#requirements)
- [Remove prior versions](#remove-prior-versions)
- [Install stable version](#install-stable-version)
- [Add Plugin](#add-plugin)
- [Add Tracking](#add-tracking)
- [Removing Tealium (optional)](#removing-tealium-optional)

### Requirements ###

* PhoneGap 3.3

### Remove Prior Versions
Using the CLI:
```
sudo npm remove -g phonegap
```

### Install Stable Version
As of the time of this writing, 3.3.0 is the most stable version. 3.0.x and 3.4.x had bugs that prevent plugins from properly working.
```
sudo npm install -g phonegap@3.3.0-0.19.6
```

### Add Plugin
From the CLI, first:

1. ```phonegap create /PATH_TO_PROJECT```
2. ```cd in to project```
3. ```phonegap build PLATFORM``` (where PLATFORM is ios,android)
4. ```phonegap local plugin add /PATH_TO_TEALIUM_PLUGIN/```
5. ```phonegap build PLATFORM``` (again)

Then init the library in your project:

```javascript
tealium.init({
	account : "tealiummobile" 		// REQUIRED: Your account.
    , profile : "demo" 				// REQUIRED: Profile you wish to use.
    , environment : "dev" 			// REQUIRED: "dev", "qa", or "prod".
    , disableHTTPS : false 			// OPTIONAL: Default is false.
    , suppressLogs : true 			// OPTIONAL: Default is true.
    , suppressErrors : false 		// OPTIONAL: Default is false, doesn't affect iOS.
	, disableLifeCycleTrack : false	// OPTIONAL: Default is false.
});
```

### Add Tracking
The following is an example of how to track events or view changes:

```javascript
tealium.track("view", // "view" or "link"
	{ "custom_key" : "custom_val" } // Object containing key-value pairs.
);
```

## Removing Tealium (Optional)

```
phonegap local plugin remove /PATH_TO_TEALIUM_PLUGIN/
```
> ```phonegap plugin list``` can help you find the plugin names

