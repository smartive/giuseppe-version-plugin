# giuseppe-version-plugin

This is a plugin for [giuseppe](http://giuseppe.smartive.ch).
This plugin adds a `@Version` route modificator to add versioning to an api.

[![Coverage Status](https://coveralls.io/repos/github/smartive/giuseppe-version-plugin/badge.svg)](https://coveralls.io/github/smartive/giuseppe-version-plugin)
[![Build Status](https://travis-ci.org/smartive/giuseppe-version-plugin.svg?branch=master)](https://travis-ci.org/smartive/giuseppe-version-plugin)
[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release)
[![npm](https://img.shields.io/npm/v/giuseppe-version-plugin.svg?maxAge=3600)](https://www.npmjs.com/package/giuseppe-version-plugin)

## Installation

To install this package, simply run

`npm i giuseppe-version-plugin -S`

## How to use

Here is a brief example of how to add the plugin to giuseppe:

```typescript
import { Giuseppe } from 'giuseppe';
import { GiuseppeVersionPlugin } from 'giuseppe-version-plugin';

const app = new Giuseppe();
app.registerPlugin(new GiuseppeVersionPlugin());
app.start();
```

### Versionining

When you want to version your routes, you can use the `@Version` decorator to do so.
It is configurable, which header name should be used and from and until which version the function is valid.
When a version header can't be parsed, it defaults to V1 and if no matching version is found, a 404 is returned.

```typescript
@Controller()
export class VersionedController {
    @Version({ from: 1, until: 1 })
    @Get()
    public functionV1(): string {
        return 'hello from v1';
    }
    
    @Version({ from: 2, until: 4 })
    @Get()
    public functionV2UntilV4(): string {
        return 'hello from v2 until v4';
    }
    
    @Version({ from: 5 })
    @Get()
    public functionV5(): string {
        return 'hello from v5 until Infinity.';
    }
}
```

The default header is `Accept-Version`.

## Changelog

The changelog is generated by [semantic release](https://github.com/semantic-release/semantic-release) and is located under the 
[release section](https://github.com/smartive/giuseppe-version-plugin/releases).

## Licence

This software is licenced under the [MIT](LICENSE) licence.
