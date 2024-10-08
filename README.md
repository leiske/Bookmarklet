# Bookframe

Bookframe speeds up the development cycle of [bookmarklets](https://wikipedia.org/wiki/Bookmarklet) by providing hot reload, small helper functions, and an install page generator.

Built with Bun, Bookframe is a new take on the classic bookmarklet development process.

### Usage

Install Bookframe: `bun add bookframe` or if you just want the CLI: `bunx bookframe`

(It also works with `npm`: `npm install bookframe` or `npx bookframe`)

#### Development

1. Create a new JavaScript (or TypeScript) file: `echo 'alert("Hello, world!")' >> bookmarklet.ts`
2. Run the Bookframe development server passing in your code: `bookframe dev bookmarklet.ts`
3. Open `http://localhost:3000/install` in your browser to install the bookmarklet.
4. Click your bookmark and watch each run use your latest code.

> [!NOTE]
> Some websites Content Security Policies may prevent the hot reload bookmarklet from fetching correctly. Switch to the "Production" bookmarklet to avoid this issue, but you will lose the hot reload.

#### Production

Bookframe supports three methods of distributing your bookmarklet:

1. Standalone code output: `bookframe build bookmarklet.ts`
    * good when you just want the dang thing in stdout
2. Installer page output: `bookframe build bookmarklet.ts --installer` (WIP)
    * good for hosting on a website for easy distribution
3. Embeddable button output: `bookframe build bookmarklet.ts --button`
    * good for sharing on a wiki page or a blog

### Included Helpers

For faster bookmarklet development, Bookframe includes a few helper functions.
I found these were the common tasks I was writing in my bookmarklets, so I included them in Bookframe.

Aren't using them? No worries - your bookmarklets won't be bloated with unused code.

#### `copyToClipboard`

```typescript
import { copyToClipboard } from 'bookframe/helpers';
copyToClipboard('Hello, world!')
```

#### `toast`

```typescript
import { toast } from 'bookframe/helpers';
toast('Hello, world!')
```

#### Cookies

```typescript
import { getCookieValue, setCookieValue } from 'bookframe/helpers';
const val = getCookieValue('oldCookie');
setCookieValue('newCookie', val, 2); // expires in 2 days
```
