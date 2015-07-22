# css loader for webpack

I forked this module because I use it with SASS and webpack prerendering. Thus, modules didn't work and I kept getting this error message because the class names were different on the frontend than the ones in the backend:

```
Warning: React attempted to reuse markup in a container but the checksum was invalid. This generally means that you are using server rendering and the markup generated on the server was not what the client was expecting. React injected new markup to compensate which works but you have lost many of the benefits of server rendering. Instead, figure out why the markup being generated is different on the client or server:
```

So I fixed it by adding 1 new parameter to localIdentName: `sourceHash`.

## Usage

Use `[sourceHash]` or `[sourceHash:keyLen]` to make css-loader generate the same classes for the same localName and source code combination.

## Example

```
const CSS_LOADER_PARAMS = `modules&localIdentName=${DEBUG ? '[dir]--[local]--[sourceHash:5]' : '[sourceHash]&minimize'}`;

// Frontend
loader: `style!css?${CSS_LOADER_PARAMS}&sourceMap!autoprefixer!${SASS_LOADER}`

// Prerendered
loader: `css/locals?${CSS_LOADER_PARAMS}!autoprefixer!${SASS_LOADER}`
```

## Docs

[Original Docs](https://github.com/webpack/css-loader)

## License

MIT (http://www.opensource.org/licenses/mit-license.php)
