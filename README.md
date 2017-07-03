# giuseppe-version-plugin

This is a plugin for [giuseppe](http://giuseppe.smartive.ch).
Giuseppe plugin that adds a ´@Version´ route modificator to add versioning to an api.

## Installation

To install this package, simply run

`npm i giuseppe-version-plugin -S`

## How to use

*How to use the plugin.*
Here is a brief example of how to add the plugin to giuseppe:
```typescript
import { Giuseppe } from 'giuseppe';
import { GiuseppeVersionPlugin } from 'giuseppe-version-plugin';

const app = new Giuseppe();
app.registerPlugin(new GiuseppeVersionPlugin());
app.start();
```

## Changelog

The changelog is based on [keep a changelog](http://keepachangelog.com) and is located here:

[Changelog](CHANGELOG.md)
