# giuseppe-version-plugin

This is a plugin for [giuseppe](http://giuseppe.smartive.ch).
This plugin adds a `@Version` route modificator to add versioning to an api.

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

The changelog is based on [keep a changelog](http://keepachangelog.com) and is located here:

[Changelog](CHANGELOG.md)

## Licence

This software is licenced under the [MIT](LICENSE) licence.
