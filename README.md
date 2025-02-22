<div align="center">
	<a  href="https://www.storyblok.com?utm_source=github.com&utm_medium=readme&utm_campaign=storyblok-js-client"  align="center">
		<img  src="https://a.storyblok.com/f/88751/1776x360/4d075611c6/sb-js-sdk.png"  alt="Storyblok Logo">
	</a>
	<h1 align="center">Universal JavaScript SDK for Storyblok's API</h1>
	<p align="center">This client is a thin wrapper for the <a href="http://www.storyblok.com?utm_source=github.com&utm_medium=readme&utm_campaign=storyblok-js-client" target="_blank">Storyblok</a> API's to use in Node.js and the browser.</p>
</div>

<p align="center">
  <a href="https://npmjs.com/package/storyblok-js-client">
    <img src="https://img.shields.io/npm/v/storyblok-js-client/latest.svg?style=flat-square&color=09b3af" alt="Storyblok JS Client" />
  </a>
  <a href="https://npmjs.com/package/storyblok-js-client" rel="nofollow">
    <img src="https://img.shields.io/npm/dt/storyblok-js-client.svg?style=appveyor&color=09b3af" alt="npm">
  </a>
  <a href="https://discord.gg/jKrbAMz">
   <img src="https://img.shields.io/discord/700316478792138842?label=Join%20Our%20Discord%20Community&style=appveyor&logo=discord&color=09b3af">
   </a>
  <a href="https://twitter.com/intent/follow?screen_name=storyblok">
    <img src="https://img.shields.io/badge/Follow-%40storyblok-09b3af?style=appveyor&logo=twitter" alt="Follow @Storyblok" />
  </a><br/>
  <a href="https://app.storyblok.com/#!/signup?utm_source=github.com&utm_medium=readme&utm_campaign=storyblok-js-client">
    <img src="https://img.shields.io/badge/Try%20Storyblok-Free-09b3af?style=appveyor&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAABGdBTUEAALGPC/xhBQAAADhlWElmTU0AKgAAAAgAAYdpAAQAAAABAAAAGgAAAAAAAqACAAQAAAABAAAAHqADAAQAAAABAAAAHgAAAADpiRU/AAACRElEQVRIDWNgGGmAEd3D3Js3LPrP8D8WXZwSPiMjw6qvPoHhyGYwIXNAbGpbCjbzP0MYuj0YFqMroBV/wCxmIeSju64eDNzMBJUxvP/9i2Hnq5cM1devMnz984eQsQwETeRhYWHgIcJiXqC6VHlFBjUeXgav40cIWkz1oLYXFmGwFBImaDFBHyObcOzdW4aSq5eRhRiE2dgYlpuYoYSKJi8vw3GgWnyAJIs/AuPu4scPGObd/fqVQZ+PHy7+6udPOBsXgySLDfn5GRYYmaKYJcXBgWLpsx8/GPa8foWiBhuHJIsl2DkYQqWksZkDFgP5PObcKYYff//iVAOTIDlx/QPqRMb/YSYBaWlOToZIaVkGZmAZSQiQ5OPtwHwacuo4iplMQEu6tXUZMhSUGDiYmBjylFQYvv/7x9B04xqKOnQOyT5GN+Df//8M59ASXKyMHLoyDD5JPtbj42OYrm+EYgg70JfuYuIoYmLs7AwMjIzA+uY/zjAnyWJpDk6GOFnCvrn86SOwmsNtKciVFAc1ileBHFDC67lzG10Yg0+SjzF0ownsf/OaofvOLYaDQJoQIGix94ljv1gIZI8Pv38zPvj2lQWYf3HGKbpDCFp85v07NnRN1OBTPY6JdRSGxcCw2k6sZuLVMZ5AV4s1TozPnGGFKbz+/PE7IJsHmC//MDMyhXBw8e6FyRFLv3Z0/IKuFqvFyIqAzd1PwBzJw8jAGPfVx38JshwlbIygxmYY43/GQmpais0ODDHuzevLMARHBcgIAQAbOJHZW0/EyQAAAABJRU5ErkJggg==" alt="Follow @Storyblok" />
  </a>
</p>

## 🚀 Usage

### Install

```sh
npm install storyblok-js-client # yarn add storyblok-js-client
```

#### Compatibility

| Version to install                                                                                                              | Support                                              |
| ------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| Latest `storyblok-js-client`                                                                                                    | Modern browsers + Node 18+                           |
| Latest `storyblok-js-client` <br> + Fetch polyfill like [isomorphic-fetch](https://github.com/matthew-andrews/isomorphic-fetch) | Browsers and Node versions with no Fetch API support |
| [Version 4](https://github.com/storyblok/storyblok-js-client/tree/v4.5.8) `storyblok-js-client@4`                               | Internet Explorer support                            |

### How to use it

#### Using the Content Deliver API

```javascript
// 1. Import the Storyblok client
import StoryblokClient from "storyblok-js-client";

// 2. Initialize the client with the preview token
// from your space dashboard at https://app.storyblok.com
const Storyblok = new StoryblokClient({
  accessToken: <YOUR_SPACE_ACCESS_TOKEN>,
});
```

#### Using the Content Management API

```javascript
// 1. Import the Storyblok client
import StoryblokClient from "storyblok-js-client";
const spaceId = <YOUR_SPACE_ID>;

// 2. Initialize the client with the oauth token
// from the my account area at https://app.storyblok.com
const Storyblok = new StoryblokClient({
  oauthToken: <YOUR_OAUTH_TOKEN>,
});

Storyblok.post(`spaces/${spaceId}/stories`, {
  story: { name: "xy", slug: "xy" },
});
Storyblok.put(`spaces/${spaceId}/stories/1`, {
  story: { name: "xy", slug: "xy" },
});
Storyblok.delete(`spaces/${spaceId}/stories/1`, null);
```

#### Using the RichTextResolver separately

You can import and use the `RichTextResolver` directly:

```js
import RichTextResolver from 'storyblok-js-client/richTextResolver'

const resolver = new RichTextResolver()

const html = resolver.render(data)
```

### NEW BRANCHES AND VERSIONS

The old master branch containing version `4.x.y` has been moved to the `v4` branch.
We’ve renamed the `master` branch to `main` and now it contains version 5.0.0.
If you wish to continue using the non Typescript version with `axios`, please use version `4`. You can install it by running `npm install https://github.com/storyblok/storyblok-js-client.git#4.x.x`.

### BREAKING CHANGES - FROM VERSION 5

### Added TypeScript - Version 5

We added TypeScript to our codebase, improving our code quality and assuring the correct implementation from the client's side. This change will probably break your code, because your Storyblok client's current implementation is possibly sending the wrong types to the source.
All the types are declared under `types`. If you use an IDE to code, you'll be able to hover the problematic cause and see what is being expected from the type. Yet, you can keep using our version without TypeScript.

### Axios removal - Version 5

We removed our dependency on axios in Version `5`. If you want to continue using our SDK with axios, please use version `4`.
The proxy feature was also removed in this version.

### Fetch (use polyfill if needed) - Version 5

Version 5 is using native `fetch` API, supported by modern browsers and Node 17.5+. If you are using an environment with no `fetch` API support, you can use a polyfill like [isomorphic-fetch](https://github.com/matthew-andrews/isomorphic-fetch) at the very beginning of your app entry point:

```js
import 'isomorphic-fetch'
require('isomorphic-fetch') // in CJS environments
```

## Documentation

#### Assets structure compatibility

We added retro-compatibility when using `resolve_assets: 1` parameter under V2. Now, if you are using our V2 client, you should receive the assets structure just the same as V1.

### Documentation

#### Class `Storyblok`

**Parameters**

- `config` Object
  - `accessToken` String, The preview token you can find in your space dashboard at https://app.storyblok.com
  - `cache` Object
    - `type` String, `none` or `memory`
  - (`responseInterceptor` Function, optional - You can pass a function and return the result. For security reasons, Storyblok client will deal only with the response interceptor.)
  - (`region` String, optional)
  - (`https` Boolean, optional)
  - (`rateLimit` Integer, optional, defaults to 3 for management api and 5 for cdn api)
  - (`timeout` Integer, optional)
  - (`maxRetries` Integer, optional, defaults to 5)
  - (`richTextSchema` Object, optional - your custom schema for RichTextRenderer)
- (`endpoint` String, optional)

#### Activating request cache

The Storyblok client comes with a caching mechanism.
When initializing the Storyblok client you can define a cache provider for caching the requests in memory.
To clear the cache you can call `Storyblok.flushCache()` or activate the automatic clear with clear: 'auto'.

```javascript
let Storyblok = new StoryblokClient({
  accessToken: <YOUR_SPACE_ACCESS_TOKEN>,
  cache: {
    clear: "auto",
    type: "memory",
  },
});
```

#### Passing response interceptor

The Storyblok client lets you pass a function that serves as a response interceptor to it.
Usage:

```javascript
let Storyblok = new StoryblokClient({
  accessToken: <YOUR_SPACE_ACCESS_TOKEN>,
  cache: {
    clear: "auto",
    type: "memory",
  },
  responseInterceptor: (response) => {
    // one can handle status codes and more with the response
    if (response.status === 200) {
      // handle your status here
    }
    // ALWAYS return the response
    return response;
  },
});
```

### Removing response interceptor

One can remove the reponseInterceptor at any time, by calling the function `ejectInterceptor` as shown below:

```javascript
Storyblok.ejectInterceptor()
```

### Method `Storyblok#get`

With this method you can get single or multiple items. The multiple items are paginated and you will receive 25 items per page by default. If you want to get all items at once use the `getAll` method.

**Parameters**

- `[return]` Promise, Object `response`
- `path` String, Path (can be `cdn/stories`, `cdn/tags`, `cdn/datasources`, `cdn/links`)
- `options` Object, Options can be found in the [API documentation](https://www.storyblok.com/docs/api/content-delivery?utm_source=github.com&utm_medium=readme&utm_campaign=storyblok-js-client).

**Example**

```javascript
Storyblok.get('cdn/stories/home', {
	version: 'draft',
})
	.then((response) => {
		console.log(response)
	})
	.catch((error) => {
		console.log(error)
	})
```

#### Method `Storyblok#getAll`

With this method you can get all items at once.

**Parameters**

- `[return]` Promise, Array of entities
- `path` String, Path (can be `cdn/stories`, `cdn/tags`, `cdn/datasources`, `cdn/links`)
- `options` Object, Options can be found in the [API documentation](https://www.storyblok.com/docs/api/content-delivery?utm_source=github.com&utm_medium=readme&utm_campaign=storyblok-js-client).
- `entity` String, Storyblok entity like stories, links or datasource. It's optional.

**Example**

```javascript
Storyblok.getAll('cdn/stories', {
	version: 'draft',
})
	.then((stories) => {
		console.log(stories) // an array
	})
	.catch((error) => {
		console.log(error)
	})
```

#### Method `Storyblok#post` (only management api)

**Parameters**

- `[return]` Promise, Object `response`
- `path` String, Path (`spaces/*`, ... see more at https://www.storyblok.com/docs/management-api/authentication?utm_source=github.com&utm_medium=readme&utm_campaign=storyblok-js-client)
- `payload` Object

**Example**

```javascript
Storyblok
  .post('spaces/<YOUR_SPACE_ID>/stories', {
    story: {name 'xy', slug: 'xy'}
  })
  .then((response) => {
    console.log(response);
  })
  .catch((error) => {
    console.log(error);
  })
```

#### Method `Storyblok#put` (only management api)

**Parameters**

- `[return]` Promise, Object `response`
- `path` String, Path (`spaces/*`, ... see more at https://www.storyblok.com/docs/management-api/authentication?utm_source=github.com&utm_medium=readme&utm_campaign=storyblok-js-client)
- `payload` Object

**Example**

```javascript
Storyblok
  .put('spaces/<YOUR_SPACE_ID>/stories/1', {
    story: {name 'xy', slug: 'xy'}
  })
  .then((response) => {
    console.log(response);
  })
  .catch((error) => {
    console.log(error);
  })
```

#### Method `Storyblok#delete` (only management api)

**Parameters**

- `[return]` Promise, Object `response`
- `path` String, Path (`spaces/*`, ... see more at https://www.storyblok.com/docs/management-api/authentication)
- `payload` Object

**Example**

```javascript
Storyblok.delete('spaces/<YOUR_SPACE_ID>/stories/1', null)
	.then((response) => {
		console.log(response)
	})
	.catch((error) => {
		console.log(error)
	})
```

#### Method `Storyblok#flushCache`

**Parameters**

- `[return]` Promise, Object returns the Storyblok client

**Example**

```javascript
Storyblok.flushCache()
```

#### Method `Storyblok#setComponentResolver`

**Parameters**

- `callback` Function, Render function to render components of the richtext field

Option 1: Use a switch case definition to render different components:

```javascript
Storyblok.setComponentResolver((component, blok) => {
	switch (component) {
		case 'my-custom-component':
			return `<div class="my-component-class">${blok.text}</div>`
			break
		case 'my-header':
			return `<h1 class="my-class">${blok.title}</h1>`
			break
		default:
			return 'Resolver not defined'
	}
})
```

Option 2: Dynamically render a component (Example in Vue.js):

```javascript
Storyblok.setComponentResolver((component, blok) => {
	return `<component :blok='${JSON.stringify(blok)}'
                     is="${component}"></component>`
})
```

#### Method `Storyblok#richTextResolver.render`

**Parameters**

- `[return]` String, Rendered html of a richtext field
- `data` Richtext object, An object with a `content` (an array of nodes) field.

**Example**

```javascript
Storyblok.richTextResolver.render(blok.richtext)
```

### Code examples

#### Filter by content type values and path

```javascript
import StoryblokClient from "storyblok-js-client";

let client = new StoryblokClient({
  accessToken: <YOUR_SPACE_ACCESS_TOKEN>,
});

// Filter by boolean value in content type
client
  .get("cdn/stories", {
    version: "draft",
    filter_query: {
      is_featured: {
        in: true,
      },
    },
  })
  .then((res) => {
    console.log(res.data.stories);
  });

// Get all news and author contents
client
  .get("cdn/stories", {
    version: "draft",
    filter_query: {
      component: {
        in: "news,author",
      },
    },
  })
  .then((res) => {
    console.log(res.data.stories);
  });

// Get all content from the news folder
client
  .get("cdn/stories", {
    version: "draft",
    starts_with: "news/",
  })
  .then((res) => {
    console.log(res.data.stories);
  });
```

#### Download all content from Storyblok

Following a code example using the storyblok-js-client to backup all content on your local filesystem inside a 'backup' folder.

```javascript
import StoryblokClient from "storyblok-js-client";
import fs from "fs";

let client = new StoryblokClient({
  accessToken: <YOUR_SPACE_ACCESS_TOKEN>,
});

let lastPage = 1;
let getStories = (page) => {
  client
    .get("cdn/stories", {
      version: "draft",
      per_page: 25,
      page: page,
    })
    .then((res) => {
      let stories = res.data.stories;
      stories.forEach((story) => {
        fs.writeFile(
          "./backup/" + story.id + ".json",
          JSON.stringify(story),
          (err) => {
            if (err) throw err;

            console.log(story.full_slug + " backed up");
          }
        );
      });

      let total = res.total;
      lastPage = Math.ceil(res.total / res.perPage);

      if (page <= lastPage) {
        page++;
        getStories(page);
      }
    });
};

getStories(1);
```

#### Initialize with a proxy server

```javascript
const proxy = {
  host: host,
  port: port,
  auth: {
    username: 'username',
    password: 'password'
  }
}

const storyblok = new StoryblokClient({
  ...
  https: false,
  proxy: proxy
})
```

Read more about proxy settings in axios [documentation](https://github.com/axios/axios)

#### How to define a custom schema for the RichTextRenderer

To define how to add some classes to specific html attributes rendered by the rich text renderer, you need your own schema definition. With this new schema, you can pass it as the `richTextSchema` option when instantiate the `StoryblokClient` class. You **must** follow the [default schema](https://github.com/storyblok/storyblok-js-client/blob/master/source/schema.js) to do this.

Below, you can check an example:

```javascript
import StoryblokClient from "storyblok-js-client";

// the default schema copied and updated
import MySchema from "./my-schema";

let client = new StoryblokClient({
  accessToken: <YOUR_SPACE_ACCESS_TOKEN>,
  richTextSchema: MySchema,
});

client.richTextResolver.render(data);
```

If you just want to change the way a specific tag is rendered you can import the default schema and extend it. Following an example that will render headlines with classes:

Instead of `<p>Normal headline</p><h3><span class="margin-bottom-fdsafdsada">Styled headline</span></h3>` it will render `<p>Normal headline</p><h3 class="margin-bottom-fdsafdsada">Styled headline</h3>`.

```javascript
import RichTextResolver from 'storyblok-js-client/richTextResolver'
import MySchema from 'storyblok-js-client/schema'

MySchema.nodes.heading = function (node) {
	let attrs = {}

	if (
		node.content &&
		node.content.length === 1 &&
		node.content[0].marks &&
		node.content[0].marks.length === 1 &&
		node.content[0].marks[0].type === 'styled'
	) {
		attrs = node.content[0].marks[0].attrs
		delete node.content[0].marks
	}

	return {
		tag: [
			{
				tag: `h${node.attrs.level}`,
				attrs: attrs,
			},
		],
	}
}

let rteResolver = new RichTextResolver(MySchema)
let rendered = rteResolver.render({
	content: [
		{
			content: [
				{
					text: 'Normal headline',
					type: 'text',
				},
			],
			type: 'paragraph',
		},
		{
			attrs: {
				level: 3,
			},
			content: [
				{
					marks: [
						{
							attrs: {
								class: 'margin-bottom-fdsafdsada',
							},
							type: 'styled',
						},
					],
					text: 'Styled headline',
					type: 'text',
				},
			],
			type: 'heading',
		},
	],
	type: 'doc',
})

console.log(rendered)
```

## 🔗 Related Links

- **[Storyblok & Javascript on GitHub](https://github.com/search?q=org%3Astoryblok+topic%3Ajavascript)**: Check all of our Javascript open source repos;
- **[Technology Hub](https://www.storyblok.com/technologies?utm_source=github.com&utm_medium=readme&utm_campaign=storyblok-js-client)**: We prepared technology hubs so that you can find selected beginner tutorials, videos, boilerplates, and even cheatsheets all in one place;
- **[Storyblok CLI](https://github.com/storyblok/storyblok)**: A simple CLI for scaffolding Storyblok projects and fieldtypes.

## ℹ️ More Resources

### Support

- Bugs or Feature Requests? [Submit an issue](../../../issues/new);

- Do you have questions about Storyblok or you need help? [Join our Discord Community](https://discord.gg/jKrbAMz).

### Contributing

Please see our [contributing guidelines](https://github.com/storyblok/.github/blob/master/contributing.md) and our [code of conduct](https://www.storyblok.com/trust-center#code-of-conduct?utm_source=github.com&utm_medium=readme&utm_campaign=storyblok-js-client).
This project use [semantic-release](https://semantic-release.gitbook.io/semantic-release/) for generate new versions by using commit messages and we use the Angular Convention to naming the commits. Check [this question](https://semantic-release.gitbook.io/semantic-release/support/faq#how-can-i-change-the-type-of-commits-that-trigger-a-release) about it in semantic-release FAQ.
