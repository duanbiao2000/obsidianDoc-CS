## Next.js 新手到高手必备100个实战练习（附答案）

这份练习集旨在通过100个精心设计的、循序渐进的实战任务，帮助你从Next.js新手成长为能够驾驭复杂企业级项目的高手。所有练习都围绕最新的Next.js特性（如App Router, Server Components, Server Actions等）展开，侧重于解决工程实践中的真实问题。

---

### **第一部分：入门基础 (练习 1-25)**

本阶段重点掌握Next.js的基础设置、App Router的核心概念以及基本组件的构建。

**环境与项目搭建**
1.  **练习 1: 初始化项目**
    *   **要求**: 使用`create-next-app`创建一个新的Next.js项目，包含TypeScript, ESLint和Tailwind CSS。
    *   **答案**: 在终端运行 `npx create-next-app@latest my-app --typescript --eslint --tailwind`。

2.  **练习 2: 运行与调试**
    *   **要求**: 成功启动开发服务器并能在浏览器中看到默认欢迎页面。
    *   **答案**: `cd my-app` 然后运行 `npm run dev`。在浏览器打开 `http://localhost:3000`。

3.  **练习 3: 理解项目结构**
    *   **要求**: 解释 `app`, `public`, 和 `next.config.mjs` 目录及文件的作用。
    *   **答案**: `app` 是App Router的核心，用于定义路由和页面。`public` 用于存放静态资源（如图片、favicon）。`next.config.mjs` 是Next.js的配置文件。

**App Router基础**
4.  **练习 4: 创建第一个页面**
    *   **要求**: 创建一个 `/about` 路由，页面显示 "关于我们"。
    *   **答案**: 在 `app` 目录下创建 `about` 文件夹，然后在其中创建 `page.tsx` 文件，并导出一个返回 `<h1>关于我们</h1>` 的React组件。

5.  **练习 5: 创建嵌套路由**
    *   **要求**: 创建一个 `/dashboard/settings` 路由。
    *   **答案**: 在 `app` 目录下创建 `dashboard` 文件夹，再在 `dashboard` 内创建 `settings` 文件夹，最后在 `settings` 内创建 `page.tsx`。

6.  **练习 6: 理解 `layout.tsx`**
    *   **要求**: 创建一个全局的`Header`组件，并让它显示在所有页面上。
    *   **答案**: 在 `app` 目录下创建 `components/Header.tsx` 组件。然后在根目录 `app/layout.tsx` 中导入并将其放置在 `{children}` 之前。

7.  **练习 7: 创建嵌套布局**
    *   **要求**: 为所有 `/dashboard/` 下的路由创建一个侧边栏布局，但不影响其他页面。
    *   **答案**: 在 `app/dashboard` 目录下创建 `layout.tsx` 文件，并在其中实现侧边栏布局结构，将 `{children}` 放置在主内容区域。

8.  **练习 8: 页面导航 (`<Link>`)**
    *   **要求**: 在首页添加两个链接，分别指向 `/about` 和 `/dashboard/settings`。
    *   **答案**: 在 `app/page.tsx` 中，从 `next/link` 导入 `Link` 组件，并使用 `<Link href="/about">关于</Link>` 和 `<Link href="/dashboard/settings">设置</Link>`。

**组件与样式**
9.  **练习 9: 使用Tailwind CSS**
    *   **要求**: 使用Tailwind CSS工具类将首页标题居中并设置为蓝色大号字体。
    *   **答案**: 在 `app/page.tsx` 的 `<h1>` 标签上添加className: `<h1 className="text-3xl font-bold text-blue-500 text-center">`。

10. **练习 10: 使用CSS Modules**
    *   **要求**: 创建一个按钮组件，其样式使用CSS Modules定义，确保样式隔离。
    *   **答案**: 创建 `components/Button.module.css` 和 `components/Button.tsx`。在组件中导入样式 `import styles from './Button.module.css'`，并使用 `<button className={styles.myButton}>`。

11. **练习 11: 全局CSS**
    *   **要求**: 在 `app/globals.css` 中设置全局的 `body` 背景色。
    *   **答案**: 打开 `app/globals.css` 文件，在 `body` 选择器中添加 `background-color: #f0f2f5;`。

12. **练习 12: 服务端组件 (RSC) vs 客户端组件**
    *   **要求**: 创建一个显示当前时间的服务端组件，和一个点击会alert的客户端组件。
    *   **答案**:
        *   **服务端组件**: `app/components/ServerTime.tsx` - `export default function ServerTime() { return <p>Server Time: {new Date().toLocaleTimeString()}</p>; }` (默认是服务端组件)。
        *   **客户端组件**: `app/components/AlertButton.tsx` - 在文件顶部添加 `'use client';`，然后创建一个包含 `onClick={() => alert('Clicked!')}` 的按钮。

13. **练习 13: 静态资源处理 (`Image` 组件)**
    *   **要求**: 在 `public` 目录放一张图片，并在首页使用 `next/image` 的 `Image` 组件显示它，并添加 `alt` 属性。
    *   **答案**: 将图片（如 `logo.png`）放入 `public` 文件夹。在 `app/page.tsx` 中 `import Image from 'next/image';` 并使用 `<Image src="/logo.png" alt="My Logo" width={100} height={50} />`。

**数据获取**
14. **练习 14: 在服务端组件中获取数据**
    *   **要求**: 创建一个 `/posts` 页面，使用 `fetch` 从 JSONPlaceholder API (`/posts/1`) 获取一篇文章并在页面上展示其标题和内容。
    *   **答案**: 在 `app/posts/page.tsx` 中，将组件声明为 `async function`，然后在组件内部使用 `const res = await fetch(...)` 和 `const data = await res.json()` 来获取数据并渲染。

15. **练习 15: 动态路由**
    *   **要求**: 创建一个动态路由 `/posts/[id]`，使其能根据URL中的 `id` 获取并显示对应文章的数据。
    *   **答案**: 创建目录结构 `app/posts/[id]/page.tsx`。组件的props会接收到 `params` 对象，从中可以解构出 `id` (`{ params: { id } }`)。使用这个 `id` 来fetch对应的数据。

16. **练习 16: 生成静态参数 (`generateStaticParams`)**
    *   **要求**: 为 `/posts/[id]` 路由预渲染前10篇文章，以提升构建时的静态生成性能。
    *   **答案**: 在 `app/posts/[id]/page.tsx` 文件中，导出一个 `async function generateStaticParams()`，该函数fetch前10篇文章并返回一个包含 `id` 的对象数组，如 `[{ id: '1' }, { id: '2' }, ...]`。

**路由处理**
17. **练习 17: `loading.tsx` 文件**
    *   **要求**: 为 `/posts` 路由添加一个加载状态UI。当数据获取较慢时，显示 "Loading posts..."。
    *   **答案**: 在 `app/posts` 目录下创建 `loading.tsx` 文件，并导出一个组件，该组件将作为数据加载期间的UI占位符。

18. **练习 18: `error.tsx` 文件**
    *   **要求**: 为 `/posts/[id]` 路由添加错误处理。当fetch失败或文章不存在时，显示一个友好的错误信息。
    *   **答案**: 在 `app/posts/[id]` 目录下创建 `error.tsx` 文件（这是一个客户端组件），它会接收 `error` 和 `reset` 作为props，用于展示错误信息并提供重试功能。

19. **练习 19: `not-found.tsx` 文件**
    *   **要求**: 当访问一个不存在的文章（如 `/posts/9999`）时，显示一个自定义的404页面。
    *   **答案**: 在数据获取函数中判断，如果文章不存在，调用 `notFound()` 函数（从 `next/navigation` 导入）。同时，在 `app/posts` 目录下创建 `not-found.tsx` 来定义自定义的404 UI。

20. **练习 20: 路由组 (`(...)`)**
    *   **要求**: 创建两个逻辑上独立的区域 `(marketing)` 和 `(shop)`，它们共享根布局，但有各自的子布局。
    *   **答案**: 在 `app` 目录下创建 `(marketing)` 和 `(shop)` 文件夹。路由不受文件夹名称影响（例如 `app/(marketing)/about/page.tsx` 对应的路由仍是 `/about`），但可以在这些文件夹内定义各自的 `layout.tsx`。

**API 路由**
21. **练习 21: 创建简单的GET API**
    *   **要求**: 创建一个API路由 `/api/hello`，它返回一个JSON对象 `{ message: 'Hello World' }`。
    *   **答案**: 创建文件 `app/api/hello/route.ts`。在文件中导出一个 `async function GET(request: Request)`，它返回一个 `NextResponse.json({ message: 'Hello World' })`。

22. **练习 22: 创建带参数的GET API**
    *   **要求**: 创建API路由 `/api/greet`，它可以接收一个`name`查询参数，并返回 `{ message: 'Hello, [name]!' }`。
    *   **答案**: 在 `app/api/greet/route.ts` 的 `GET` 函数中，使用 `const { searchParams } = new URL(request.url)` 来获取查询参数，然后构造并返回响应。

**元数据与SEO**
23. **练习 23: 静态元数据**
    *   **要求**: 为 `/about` 页面设置静态的标题和描述。
    *   **答案**: 在 `app/about/page.tsx` 中，导出一个 `metadata` 对象：`export const metadata = { title: 'About Us', description: 'Learn more about our company.' };`。

24. **练习 24: 动态元数据**
    *   **要求**: 为 `/posts/[id]` 页面根据文章内容动态生成标题和描述。
    *   **答案**: 在 `app/posts/[id]/page.tsx` 中，导出一个 `async function generateMetadata({ params })`。在此函数中获取文章数据，并返回包含 `title` 和 `description` 的对象。

25. **练习 25: 配置 `favicon.ico`**
    *   **要求**: 为你的应用添加一个自定义的网站图标。
    *   **答案**: 将你的 `favicon.ico` 文件直接放在 `app` 目录的根目录下。Next.js 会自动识别它。

---

### **第二部分：中级实战 (练习 26-60)**

本阶段将深入探讨数据变更、用户认证、状态管理和性能优化等更复杂的工程场景。

**数据变更与Server Actions**
26. **练习 26: 创建第一个Server Action**
    *   **要求**: 创建一个简单的表单，包含一个输入框和一个按钮。点击按钮时，通过Server Action将输入框的内容打印在服务端控制台。
    *   **答案**: 在页面组件中定义一个 `async function myAction(formData: FormData)`，并在函数顶部添加 `'use server';` 指令。将此action传递给 `<form>` 的 `action` 属性。

27. **练习 27: 在客户端组件中调用Server Action**
    *   **要求**: 将练习26的表单移到一个客户端组件中，并成功调用在服务端文件中定义的Server Action。
    *   **答案**: 将Server Action定义在单独的文件中（如 `app/actions.ts`），文件顶部声明 `'use server';`。然后在客户端组件中导入并使用该action。

28. **练习 28: Server Action返回数据**
    *   **要求**: 修改Server Action，使其返回一个成功或失败的状态消息，并在客户端显示这个消息。
    *   **答案**: Server Action可以直接 `return { success: true, message: '...' }`。在客户端，可以使用 `useFormState` hook来处理action的返回状态。

29. **练习 29: 使用`useOptimistic`进行UI乐观更新**
    *   **要求**: 创建一个“点赞”按钮。点击后，立即在UI上显示点赞数+1，然后通过Server Action在后台更新数据库。
    *   **答案**: 在客户端组件中使用 `useOptimistic` hook。它会返回一个“乐观状态”，在action执行期间使用它来渲染UI。当action完成时，它会自动恢复为真实状态。

30. **练习 30: 使用`revalidatePath`和`revalidateTag`**
    *   **要求**: 创建一个添加新文章的表单。提交成功后，使用Server Action将数据存入数据库，并刷新文章列表页 (`/posts`) 的缓存。
    *   **答案**: 在Server Action的末尾，调用 `revalidatePath('/posts')` (从 `next/cache` 导入)。如果数据获取使用了标签，则可以调用 `revalidateTag('posts')` 来实现更精细的缓存失效。

31. **练习 31: 渐进式增强**
    *   **要求**: 确保练习26的表单在JavaScript被禁用的情况下依然可以工作。
    *   **答案**: Server Actions天然支持渐进式增强。只要 `<form>` 的 `action` 指向一个Server Action，即使没有客户端JavaScript，浏览器也会执行一次完整的页面刷新来提交表单。

32. **练习 32: 表单验证**
    *   **要求**: 为一个注册表单添加服务端验证（例如，使用Zod）。如果验证失败，将错误信息返回并显示在对应的输入框旁边。
    *   **答案**: 在Server Action中，使用Zod等库解析`formData`。如果验证失败，返回一个包含错误信息的对象。在客户端使用 `useFormState` 来接收并展示这些错误。

**状态管理**
33. **练习 33: URL作为状态管理器**
    *   **要求**: 创建一个产品列表页面，包含搜索和排序功能。将搜索关键词和排序选项保存在URL的查询参数中。
    *   **答案**: 使用 `useRouter` 和 `useSearchParams` (从 `next/navigation`) 来读取和更新URL。当用户输入或选择时，通过 `router.push` 或 `router.replace` 更新URL，并触发页面重新渲染。

34. **练习 34: 在客户端组件中使用Context**
    *   **要求**: 创建一个简单的"主题切换"功能（亮色/暗色），使用React Context在应用的不同部分共享和切换主题状态。
    *   **答案**: 创建一个 `ThemeContext.tsx` 文件（必须是客户端组件），并在根布局 `app/layout.tsx` 中使用 `ThemeProvider` 包裹 `{children}`。

35. **练习 35: 组合服务端和客户端组件管理状态**
    *   **要求**: 创建一个购物车。购物车的图标（显示商品数量）在Header（服务端组件）中，但添加商品的操作在产品页面（客户端组件）中。如何同步状态？
    *   **答案**: 这是一个经典问题。一种方案是将Header也变为客户端组件。更优的方案是：添加商品后，通过Server Action更新数据库，然后使用 `router.refresh()` 刷新当前路由，这将从服务端重新获取数据，包括Header中购物车数量。

**认证与授权**
36. **练习 36: 集成NextAuth.js**
    *   **要求**: 为你的应用添加GitHub登录功能。
    *   **答案**: 按照NextAuth.js的官方文档，配置 `[...nextauth]` API路由，设置GitHub Provider，并在应用中添加登录/登出按钮。

37. **练习 37: 保护页面路由**
    *   **要求**: 创建一个 `/dashboard` 页面，只允许已登录用户访问。
    *   **答案**: 在 `/dashboard` 页面的服务端组件中，获取session。如果session不存在，使用 `redirect('/login')` (从 `next/navigation`) 将用户重定向到登录页。

38. **练习 38: 保护API路由**
    *   **要求**: 创建一个 `/api/protected` 路由，只有登录用户才能访问并获取数据。
    *   **答案**: 在API路由处理函数中，获取session。如果session不存在，返回401或403状态码。

39. **练习 39: 在服务端组件中获取Session**
    *   **要求**: 在全局Header中，根据用户登录状态显示“登录”按钮或用户的头像和名称。
    *   **答案**: 在 `app/layout.tsx` 或Header组件中（如果它是服务端组件），直接从NextAuth.js提供的`auth()`函数获取session信息并进行条件渲染。

40. **练习 40: 中间件 (`middleware.ts`)**
    *   **要求**: 使用中间件保护所有以 `/admin` 开头的路由。
    *   **答案**: 在项目的根目录（与`app`同级）创建 `middleware.ts` 文件。在其中编写逻辑，检查请求路径是否匹配 `/admin/:path*`，并验证用户认证状态，根据结果决定是继续请求还是重定向。

**高级路由与布局**
41. **练习 41: 并行路由 (`@folder`)**
    *   **要求**: 创建一个Dashboard页面，同时展示 `@analytics` 和 `@team` 两个独立的视图。
    *   **答案**: 在 `app/dashboard` 目录下创建 `@analytics` 和 `@team` 文件夹，并在其中分别创建 `page.tsx`。然后在 `app/dashboard/layout.tsx` 中，将 `analytics` 和 `team` 作为props接收并渲染在布局的不同位置。

42. **练习 42: 拦截路由 (`(.)folder` 和 `(..)folder`)**
    *   **要求**: 创建一个图片画廊。点击缩略图时，使用Modal弹窗展示大图，同时URL更新到图片的独立页面。直接访问该URL时，则显示图片的独立页面。
    *   **答案**: 这是一个常见的拦截路由场景。在画廊页面目录下创建 `/@modal/(.)photos/[id]/page.tsx`。当在画廊内导航时，这个路由会被匹配并渲染在Modal中。

43. **练习 43: 模板 (`template.tsx`)**
    *   **要求**: 创建一个带有进入动画的页面。每次导航到该页面时，动画都应该重新播放。
    *   **答案**: 使用 `template.tsx` 而不是 `layout.tsx`。与布局不同，模板在每次导航时都会重新挂载，因此其中的状态和效果（如动画）不会被保留。

44. **练习 44: 自定义404和500页面**
    *   **要求**: 为整个应用创建自定义的“页面未找到”和“服务器错误”页面。
    *   **答案**: 在 `app` 目录的根级创建 `not-found.tsx` 和 `error.tsx` 文件。

**性能优化**
45. **练习 45: React `Suspense` 与流式渲染**
    *   **要求**: 在一个页面上，有三个独立的数据获取组件。使用 `Suspense` 包裹它们，让它们可以并行获取数据并流式传输到客户端，而不是等待所有数据都准备好。
    *   **答案**: 将每个数据获取组件（它们必须是 `async` 的）分别用 `<Suspense fallback={<p>Loading...</p>}>` 包裹起来。

46. **练习 46: 动态导入组件**
    *   **要求**: 有一个很少使用但体积很大的图表库。使用 `next/dynamic` 对其进行动态导入，只在需要时才加载。
    *   **答案**: `import dynamic from 'next/dynamic'; const HeavyChart = dynamic(() => import('../components/HeavyChart'), { ssr: false });`。`ssr: false` 确保它只在客户端渲染。

47. **练习 47: 缓存策略 (`fetch` 扩展)**
    *   **要求**: fetch一个不经常变动的数据列表，并设置其缓存有效期为1小时。
    *   **答案**: 在 `fetch` 调用中添加配置对象：`fetch(url, { next: { revalidate: 3600 } })`。

48. **练习 48: 按需ISR (增量静态再生)**
    *   **要求**: 创建一个Webhook API路由。当CMS内容更新时，调用此API，并根据传入的ID或标签，精确地使对应页面的缓存失效。
    *   **答案**: 创建一个 `/api/revalidate` 路由，它接收请求体中的路径或标签，然后调用 `revalidatePath` 或 `revalidateTag`。

49. **练习 49: 分析打包文件 (`@next/bundle-analyzer`)**
    *   **要求**: 配置并使用 `@next/bundle-analyzer` 来分析你的应用打包后的文件大小，找出可以优化的模块。
    *   **答案**: 安装包，并在 `next.config.mjs` 中根据其文档进行配置。运行打包命令后，会生成一个可视化的分析报告。

50. **练习 50: 字体优化 (`next/font`)**
    *   **要求**: 使用 `next/font` 引入一个Google字体，以避免布局偏移 (CLS) 并优化性能。
    *   **答案**: 从 `next/font/google` 导入字体，实例化它，然后在根布局的 `<html>` 或 `<body>` 标签上应用其 `className`。

**其他**
51. **练习 51: 路由处理器 (`Route Handlers`)**
    *   **要求**: 创建一个处理 `POST` 请求的API路由，它接收JSON数据，进行处理，并返回响应。
    *   **答案**: 在 `app/api/submit/route.ts` 中，导出一个 `async function POST(request: Request)`。使用 `await request.json()` 来解析请求体。

52. **练习 52: Draft Mode (草稿模式)**
    *   **要求**: 实现一个草稿模式，允许内容编辑者在发布前通过一个安全的URL预览他们在无头CMS中所做的更改。
    *   **答案**: 创建一个API路由来启用草稿模式（通过设置cookie），并在页面组件的数据获取逻辑中检查cookie是否存在，如果存在则获取草稿内容而不是已发布内容。

53. **练习 53: MDX集成**
    *   **要求**: 配置你的Next.js项目以支持MDX，并创建一个可以使用React组件的博客文章页面。
    *   **答案**: 安装 `@next/mdx` 和相关依赖，并在 `next.config.mjs` 中进行配置。然后你可以创建 `.mdx` 文件，并像页面一样进行路由。

54. **练习 54: 使用`redirect`函数**
    *   **要求**: 创建一个旧的URL `/old-profile`，并将其永久重定向到 `/new-profile`。
    *   **答案**: 在 `app/old-profile/page.tsx` 中，从 `next/navigation` 导入 `redirect`，然后在组件中直接调用 `redirect('/new-profile')`。

55. **练习 55: 动态`opengraph-image`**
    *   **要求**: 为博客文章页面动态生成社交媒体分享卡片图片。
    *   **答案**: 在 `app/posts/[id]` 目录下创建 `opengraph-image.tsx` 文件。这个文件可以导出一个 `ImageResponse`，允许你使用类似HTML和CSS的方式来生成图片。

56. **练习 56: 动态`sitemap.xml`**
    *   **要求**: 为你的动态内容（如博客文章）自动生成站点地图。
    *   **答案**: 在 `app` 目录下创建 `sitemap.ts` 文件，导出一个 `async function sitemap()`，它获取所有动态路由并返回一个符合站点地图格式的数组。

57. **练习 57: 使用`useRouter`进行编程式导航**
    *   **要求**: 在表单提交成功后，使用代码将用户导航到另一个页面。
    *   **答案**: 在客户端组件中，从 `next/navigation` 导入 `useRouter`，获取 `router` 实例，然后调用 `router.push('/success-page')`。

58. **练习 58: 处理Cookies**
    *   **要求**: 在Server Action或API路由中设置和读取cookie。
    *   **答案**: 从 `next/headers` 导入 `cookies`。使用 `cookies().set('name', 'value')` 和 `cookies().get('name')`。

59. **练习 59: 配置环境变量**
    *   **要求**: 创建一个 `.env.local` 文件来存储数据库连接字符串，并在服务端代码中安全地访问它。
    *   **答案**: 在 `.env.local` 中定义 `DATABASE_URL=...`。在服务端的JS/TS文件中通过 `process.env.DATABASE_URL` 访问。如果要暴露给浏览器，变量名需以 `NEXT_PUBLIC_` 开头。

60. **练习 60: 第三方库集成**
    *   **要求**: 集成一个UI组件库（如Shadcn/UI或MUI），并确保它与App Router的服务端/客户端组件模型兼容。
    *   **答案**: 遵循库的官方Next.js集成指南。关键在于识别哪些组件需要交互性（因此必须是客户端组件），并在需要的地方添加 `'use client';` 指令。

---

### **第三部分：高级与架构 (练习 61-100)**

本阶段聚焦于大型项目的架构设计、可维护性、国际化、测试和部署策略。

**架构与模式**
61. **练习 61: 项目结构组织**
    *   **要求**: 设计一个可扩展的项目结构，将组件、工具函数、类型定义、API服务等分门别类地组织。
    *   **答案**: 一种常见的结构是在项目根目录创建 `components` (UI组件), `lib` (工具函数), `types` (类型定义), `services` (API请求封装) 等文件夹。

62. **练习 62: 构建可复用的数据获取钩子**
    *   **要求**: 创建一个自定义的客户端hook `useUserData`，用于获取和缓存当前登录用户的信息。
    *   **答案**: 结合 `SWR` 或 `React Query` 库来创建这个hook，它会处理数据获取、缓存、重新验证和错误状态。

63. **练习 63: 设计一个多租户应用的路由**
    *   **要求**: 设计一个路由系统，支持 `/app/[tenantId]/...` 这样的URL结构。
    *   **答案**: 使用动态路由 `[tenantId]` 作为应用层级的根。在布局或页面中，从 `params` 中获取 `tenantId`，并将其用于所有后续的数据请求和逻辑判断。

64. **练习 64: 实现功能开关 (Feature Flags)**
    *   **要求**: 集成一个功能开关服务（如Vercel Flags或自建方案），根据开关状态动态地渲染或隐藏一个新功能。
    *   **答案**: 在服务端获取功能开关的状态，并将其作为prop传递给组件，或在组件内部直接根据状态进行条件渲染。

**国际化 (i18n)**
65. **练习 65: 设置i18n路由**
    *   **要求**: 配置应用支持英语 (`/en`) 和法语 (`/fr`) 两种语言。
    *   **答案**: 使用动态路由 `app/[lang]/page.tsx`。在中间件中检测用户偏好或URL，并重定向到合适的语言路径。

66. **练习 66: 管理翻译内容**
    *   **要求**: 实现一个加载翻译JSON文件的机制，并根据当前语言环境在组件中显示正确的文本。
    *   **答案**: 创建 `locales/en.json` 和 `locales/fr.json`。在 `[lang]` 布局或页面中加载对应的字典文件，并可以通过Context或prop传递给子组件。`next-intl` 是一个流行的库来简化这个过程。

67. **练习 67: 语言切换器**
    *   **要求**: 创建一个允许用户在不同语言之间切换的组件。
    *   **答案**: 组件生成指向不同语言版本的链接（例如，从 `/en/about` 切换到 `/fr/about`）。使用 `usePathname` 来获取当前路径（不含语言前缀）以构建新链接。

**测试**
68. **练习 68: 设置Jest和React Testing Library**
    *   **要求**: 为你的Next.js项目配置好单元测试和组件测试环境。
    *   **答案**: 遵循Next.js官方的Jest集成指南，安装必要的依赖并配置 `jest.config.js`。

69. **练习 69: 编写组件单元测试**
    *   **要求**: 为一个简单的按钮组件编写测试，验证它能被正确渲染并响应点击事件。
    *   **答案**: 使用`render`和`fireEvent`从`@testing-library/react`。`render(<Button />);` 然后 `fireEvent.click(screen.getByText('Click me'));` 并断言结果。

70. **练习 70: Mock API请求**
    *   **要求**: 测试一个获取并显示数据的组件，使用Jest的mock功能来模拟API的成功和失败响应。
    *   **答案**: 使用 `jest.spyOn` 或 `msw` (Mock Service Worker) 库来拦截 `fetch` 请求并返回预设的数据。

71. **练习 71: 测试Server Actions**
    *   **要求**: 为一个Server Action编写单元测试，验证其逻辑。
    *   **答案**: Server Actions是普通函数，可以直接导入并测试。如果它依赖数据库或其他服务，需要对这些服务进行mock。

72. **练习 72: 设置Cypress进行E2E测试**
    *   **要求**: 集成Cypress，并编写一个简单的端到端测试，模拟用户访问首页、点击链接、并验证目标页面的内容。
    *   **答案**: 遵循Next.js官方的Cypress集成指南。测试代码示例：`cy.visit('/'); cy.contains('About').click(); cy.url().should('include', '/about');`。

**部署与CI/CD**
73. **练习 73: 部署到Vercel**
    *   **要求**: 将你的GitHub仓库连接到Vercel，并实现自动部署。
    *   **答案**: 在Vercel上创建一个新项目，选择你的Git仓库，Vercel会自动检测到是Next.js项目并进行部署。之后的每次push都会触发新的部署。

74. **练习 74: 配置生产环境变量**
    *   **要求**: 在Vercel的项目设置中配置生产环境所需的API密钥等敏感信息。
    *   **答案**: 在Vercel控制台的"Settings" -> "Environment Variables"中添加变量。

75. **练习 75: 使用Docker进行自托管部署**
    *   **要求**: 编写一个`Dockerfile`来容器化你的Next.js应用（独立输出模式）。
    *   **答案**: 遵循Next.js官方文档关于Docker部署的指南。关键是在 `next.config.mjs` 中设置 `output: 'standalone'`，并在Dockerfile中正确地复制输出文件。

76. **练习 76: 实现CI/CD流水线**
    *   **要求**: 使用GitHub Actions创建一个工作流，在每次push时自动运行lint、测试和构建命令，以确保代码质量。
    *   **答案**: 在 `.github/workflows` 目录下创建一个YAML配置文件。定义触发条件（如 `on: [push]`），并设置多个job来执行 `npm run lint`, `npm test`, `npm run build`。

**剩余练习 (77-100) 涵盖更深入和具体的主题，鼓励自行探索和组合：**

1. **高级主题**: 实现一个WebSocket连接用于实时通知。
2. **高级主题**: 集成Storybook来开发和文档化UI组件。
3. **高级主题**: 创建一个复杂的、多步骤的表单，并管理其状态。
4. **架构**: 设计一个微前端架构，其中一个Next.js应用作为主容器。
5. **性能**: 实现图片的懒加载和占位符（使用Plaiceholder等库）。
6. **性能**: 分析和优化核心Web指标 (Core Web Vitals)。
7. **安全**: 实现内容安全策略 (CSP) 来防止XSS攻击。
8. **安全**: 为Server Actions添加权限检查，确保只有特定角色的用户才能执行。
9. **数据库**: 集成Prisma ORM进行类型安全的数据库操作。
10. **数据库**: 在Server Actions中实现数据库事务。
11. **可维护性**: 使用TypeScript的泛型来创建可复用的API客户端。
12. **可维护性**: 编写JSDoc或TSDoc来为你的函数和组件生成文档。
13. **部署**: 配置自定义域名和HTTPS。
14. **部署**: 实现蓝绿部署或金丝雀部署策略。
15. **监控**: 集成日志和错误监控服务（如Sentry）。
16. **监控**: 在Vercel上监控和分析函数执行情况。
17. **边缘计算**: 将一个API路由部署到Edge Runtime并理解其限制。
18. **边缘计算**: 在中间件中使用地理位置信息进行内容个性化。
19. **CMS集成**: 从一个无头CMS（如Strapi, Contentful）获取数据并渲染页面。
20. **电商**: 集成Stripe进行支付处理。
21. **AI**: 使用Vercel AI SDK创建一个简单的聊天机器人界面。
22. **综合项目**: 从头到尾构建一个功能完整的博客平台。
23. **综合项目**: 构建一个带有用户认证、商品展示和购物车的电子商务网站。
24. **重构与迁移**: 将一个使用Pages Router的旧项目迁移到App Router，并记录遇到的挑战和解决方案。
25. 

---

当然可以！以下是 **Next.js 最新版本（v14，含 App Router、Server Actions、Turbopack 等特性）的「难点 + 重点」速通问答集**，采用 **Q&A 形式**，适合快速掌握核心概念、应对面试或项目开发。

> ✅ 适用于：Next.js 13.4+ → **Next.js 14（稳定版）**，重点聚焦 **App Router、Server Components、Server Actions、Turbopack、React 18 特性集成**

---

<details>
<summary>1. Next.js 14 中 App Router 和 Pages Router 有什么区别？</summary>

**答：**

| 特性 | App Router（推荐） | Pages Router（旧） |
|------|------------------|------------------|
| 路径结构 | `app/page.tsx` | `pages/index.js` |
| 默认组件类型 | Server Components（可切换） | Client Components |
| 数据获取 | `async` Server Components | `getServerSideProps`, `getStaticProps` |
| 布局方式 | `layout.tsx` 自动嵌套 | 需手动封装 |
| 支持 Server Actions | ✅ 原生支持 | ❌ 不支持 |
| 动态路由 | `app/blog/[id]/page.tsx` | `pages/blog/[id].js` |

✅ **趋势**：App Router 是未来，官方推荐新项目使用。

</details>

---

<details>
<summary>2. Server Components 和 Client Components 的核心区别是什么？</summary>

**答：**

| 维度 | Server Components | Client Components |
|------|------------------|------------------|
| 执行环境 | 服务器端渲染 | 浏览器端执行 |
| 可用 API | 可直接访问数据库、文件系统 | 仅限浏览器 API |
| 包大小 | 不计入客户端 bundle | 计入 bundle |
| 状态与事件 | 无 useState、onClick | 支持交互逻辑 |
| 引入方式 | 默认（无需 'use client'） | 需顶部写 `'use client'` |

💡 **原则**：优先用 Server Components，仅在需要交互时加 `'use client'`。

</details>

---

<details>
<summary>3. 如何在 Server Component 中获取数据？</summary>

**答：**

直接在 `async` 组件中调用异步函数：

```tsx
// app/page.tsx
async function getData() {
  const res = await fetch('https://api.example.com/data');
  return res.json();
}

export default async function Page() {
  const data = await getData();
  return <div>{data.name}</div>;
}
```

✅ **优势**：无需 `useEffect`、`useState`，支持流式渲染（Streaming）。

</details>

---

<details>
<summary>4. 什么是 React Server Components（RSC）协议？</summary>

**答：**

RSC 是 Next.js 内部使用的私有协议，用于：
- 将 Server Component 的“结果”序列化并发送到客户端
- 客户端 React 用这些“标记”重建 UI
- 实现“零客户端 JS 打包”非交互部分

📌 **注意**：开发者无需直接操作 RSC，但它是 Server Components 的底层机制。

</details>

---

<details>
<summary>5. 如何在 Client Component 中调用 Server Action？</summary>

**答：**

Server Action 是定义在服务端的函数，可在客户端调用：

```ts
// app/actions.ts
'use server';
export async function createPost(data: FormData) {
  'use server';
  // 直接访问数据库
  await db.post.create({ data });
}
```

```tsx
// app/page.tsx (Client Component)
'use client';
import { createPost } from './actions';

export default function Form() {
  return (
    <form action={createPost}>
      <input name="title" />
      <button type="submit">发布</button>
    </form>
  );
}
```

✅ **优点**：免 API 路由，安全（自动 CSRF 保护），支持 FormData。

</details>

---

<details>
<summary>6. 如何实现动态路由？比如 /user/[id]</summary>

**答：**

使用文件夹命名：

```
app/
  user/
    [id]/
      page.tsx
```

```tsx
// app/user/[id]/page.tsx
export default function Page({ params }: { params: { id: string } }) {
  return <div>用户 ID: {params.id}</div>;
}
```

✅ 支持嵌套、可选段（`[[slug]]`）。

</details>

---

<details>
<summary>7. 如何获取搜索参数（query params）？</summary>

**答：**

使用 `useSearchParams`（Client）或 `pageProps.searchParams`（Server）：

```tsx
// Client Component
'use client';
import { useSearchParams } from 'next/navigation';

export default function Page() {
  const searchParams = useSearchParams();
  const q = searchParams.get('q');
  return <div>搜索: {q}</div>;
}
```

```tsx
// Server Component
export default function Page({ searchParams }: { searchParams: { q?: string } }) {
  return <div>搜索: {searchParams.q}</div>;
}
```

</details>

---

<details>
<summary>8. 如何实现页面嵌套路由和布局（Layout）？</summary>

**答：**

创建 `layout.tsx` 文件，自动嵌套：

```
app/
  layout.tsx          ← 全局布局
  dashboard/
    layout.tsx        ← 仅 /dashboard 下生效
    page.tsx
```

```tsx
// app/dashboard/layout.tsx
export default function DashboardLayout({
  children,
}: { children: React.ReactNode }) {
  return (
    <div>
      <h1>Dashboard Layout</h1>
      {children}
    </div>
  );
}
```

✅ 支持 `template`（每次重新渲染）、`loading.tsx`、`error.tsx`。

</details>

---

<details>
<summary>9. 如何实现加载状态（Loading）？</summary>

**答：**

在目录下创建 `loading.tsx`：

```tsx
// app/blog/loading.tsx
export default function Loading() {
  return <p>加载中...</p>;
}
```

✅ 自动在 `page.tsx` 加载时显示，支持嵌套。

</details>

---

<details>
<summary>10. 如何处理错误边界（Error UI）？</summary>

**答：**

创建 `error.tsx` 文件（必须是 Client Component）：

```tsx
'use client';
export default function Error({ error }: { error: Error }) {
  return <div>出错了：{error.message}</div>;
}
```

✅ 可捕获其子组件的渲染错误。

</details>

---

<details>
<summary>11. 如何实现静态生成（SSG）和增量静态再生（ISR）？</summary>

**答：**

在 Server Component 中导出 `generateStaticParams` 和 `revalidate`：

```tsx
// 生成静态路径
export async function generateStaticParams() {
  const posts = await db.post.findMany();
  return posts.map((post) => ({ id: post.id }));
}

// ISR：每 60 秒重新生成
export const dynamic = 'force-dynamic'; // 或 'auto'
export const revalidate = 60;
```

✅ `revalidate` > 0 启用 ISR。

</details>

---

<details>
<summary>12. 如何禁用缓存，实现动态渲染？</summary>

**答：**

设置 `dynamic` 选项：

```ts
export const dynamic = 'force-dynamic'; // 总是动态
// 或
export const dynamic = 'auto'; // 默认，有 fetch 时缓存
```

也可使用 `cache: 'no-store'`：

```ts
fetch('/api/data', { cache: 'no-store' });
```

</details>

---

<details>
<summary>13. 如何使用 Turbopack？它比 Webpack 快多少？</summary>

**答：**

Turbopack 是 Next.js 13+ 的实验性打包器（基于 Rust），启动命令：

```bash
next dev --turbo
```

✅ **优势**：
- 启动速度提升 10x~70x（尤其大型项目）
- 按需编译（on-demand)
- 原生支持 TS、JSX、CSS Modules

⚠️ 注意：生产环境仍使用 Webpack（Turbopack 生产版仍在开发中）。

</details>

---

<details>
<summary>14. 如何在 Server Action 中上传文件？</summary>

**答：**

使用 `FormData` + Server Action：

```ts
'use server';
export async function uploadFile(formData: FormData) {
  const file = formData.get('file') as File;
  const bytes = await file.arrayBuffer();
  // 保存到磁盘或云存储
}
```

```tsx
<form action={uploadFile}>
  <input type="file" name="file" />
  <button>上传</button>
</form>
```

✅ 无需 API 路由，但大文件建议用专门服务（如 S3 + presigned URL）。

</details>

---

<details>
<summary>15. 如何实现身份认证（Auth）？推荐方案？</summary>

**答：**

推荐使用 **Auth.js（原 NextAuth.js）**：

```ts
// app/api/auth/[...nextauth]/route.ts
import NextAuth from 'next-auth';
import GoogleProvider from 'next-auth/providers/google';

const handler = NextAuth({
  providers: [GoogleProvider({ clientId: '', clientSecret: '' })],
  pages: { signIn: '/login' },
});

export { handler as GET, handler as POST };
```

✅ 支持 OAuth、Credentials、Email 等多种方式。

</details>

---

<details>
<summary>16. 如何自定义 API 路由？</summary>

**答：**

在 `app/api/` 下创建路由处理程序（Route Handlers）：

```ts
// app/api/hello/route.ts
export async function GET(request: Request) {
  return Response.json({ message: 'Hello' });
}

export async function POST(request: Request) {
  const data = await request.json();
  return Response.json({ received: data });
}
```

✅ 替代旧的 `pages/api`，更贴近 Web API 标准。

</details>

---

<details>
<summary>17. 如何实现中间件（Middleware）？</summary>

**答：**

创建 `middleware.ts`：

```ts
// middleware.ts
import { NextRequest, NextFetchEvent } from 'next/server';

export function middleware(request: NextRequest) {
  const path = request.nextUrl.pathname;
  if (path === '/admin') {
    // 重定向或验证
    return Response.redirect(new URL('/login', request.url));
  }
}
```

✅ 可用于身份验证、A/B 测试、区域重定向等。

</details>

---

<details>
<summary>18. 如何优化图片？使用哪个组件？</summary>

**答：**

使用 `next/image`：

```tsx
import Image from 'next/image';

<Image
  src="/me.png"
  alt="me"
  width={300}
  height={300}
  priority
  placeholder="blur"
  blurDataURL="data:..."
/>
```

✅ 自动优化：懒加载、格式转换（WebP）、CDN 支持。

</details>

---

<details>
<summary>19. 如何实现国际化（i18n）路由？</summary>

**答：**

配置 `next.config.js`：

```js
// next.config.js
module.exports = {
  i18n: {
    locales: ['en', 'zh'],
    defaultLocale: 'zh',
  },
};
```

路径自动支持：`/en/about`、`/zh/about`

✅ 也可使用基于域名的国际化。

</details>

---

<details>
<summary>20. 如何部署 Next.js 应用？</summary>

**答：**

推荐平台：
- **Vercel**：官方团队开发，一键部署，完美支持 App Router、Server Actions
- **Netlify**、**AWS Amplify**、**Docker + Node.js 服务器**

生产构建命令：

```bash
next build
next start
```

✅ Vercel 零配置，支持边缘函数、ISR、缓存自动管理。

</details>

---

## ✅ 总结：Next.js 14 核心重点

| 类别 | 关键技术 |
|------|--------|
| 架构 | App Router、Server Components |
| 数据流 | Server Actions、`async` 组件 |
| 性能 | Turbopack（开发）、ISR、Streaming |
| 交互 | Client Components + `'use client'` |
| 部署 | Vercel、Edge Functions、Serverless |
| 生态 | Auth.js、next/image、next/font |

---

🎯 **高手建议**：
- 新项目一律使用 **App Router**
- 能用 **Server Component** 就不用 Client
- 用 **Server Actions** 替代部分 API 路由
- 开发用 **Turbopack**，生产用 Webpack（当前）
- 部署首选 **Vercel**

---

需要 **PDF 打包版、面试题合集、项目模板**，欢迎继续提问！




当然可以！以下是 **Next.js 最新版本（v14，含 App Router、Server Actions、Turbopack 等特性）的「难点 + 重点」速通问答集**，采用 **Q&A 形式**，适合快速掌握核心概念、应对面试或项目开发。

> ✅ 适用于：Next.js 13.4+ → **Next.js 14（稳定版）**，重点聚焦 **App Router、Server Components、Server Actions、Turbopack、React 18 特性集成**

---

<details>
<summary>1. Next.js 14 中 App Router 和 Pages Router 有什么区别？</summary>

**答：**

| 特性 | App Router（推荐） | Pages Router（旧） |
|------|------------------|------------------|
| 路径结构 | `app/page.tsx` | `pages/index.js` |
| 默认组件类型 | Server Components（可切换） | Client Components |
| 数据获取 | `async` Server Components | `getServerSideProps`, `getStaticProps` |
| 布局方式 | `layout.tsx` 自动嵌套 | 需手动封装 |
| 支持 Server Actions | ✅ 原生支持 | ❌ 不支持 |
| 动态路由 | `app/blog/[id]/page.tsx` | `pages/blog/[id].js` |

✅ **趋势**：App Router 是未来，官方推荐新项目使用。

</details>

---

<details>
<summary>2. Server Components 和 Client Components 的核心区别是什么？</summary>

**答：**

| 维度 | Server Components | Client Components |
|------|------------------|------------------|
| 执行环境 | 服务器端渲染 | 浏览器端执行 |
| 可用 API | 可直接访问数据库、文件系统 | 仅限浏览器 API |
| 包大小 | 不计入客户端 bundle | 计入 bundle |
| 状态与事件 | 无 useState、onClick | 支持交互逻辑 |
| 引入方式 | 默认（无需 'use client'） | 需顶部写 `'use client'` |

💡 **原则**：优先用 Server Components，仅在需要交互时加 `'use client'`。

</details>

---

<details>
<summary>3. 如何在 Server Component 中获取数据？</summary>

**答：**

直接在 `async` 组件中调用异步函数：

```tsx
// app/page.tsx
async function getData() {
  const res = await fetch('https://api.example.com/data');
  return res.json();
}

export default async function Page() {
  const data = await getData();
  return <div>{data.name}</div>;
}
```

✅ **优势**：无需 `useEffect`、`useState`，支持流式渲染（Streaming）。

</details>

---

<details>
<summary>4. 什么是 React Server Components（RSC）协议？</summary>

**答：**

RSC 是 Next.js 内部使用的私有协议，用于：
- 将 Server Component 的“结果”序列化并发送到客户端
- 客户端 React 用这些“标记”重建 UI
- 实现“零客户端 JS 打包”非交互部分

📌 **注意**：开发者无需直接操作 RSC，但它是 Server Components 的底层机制。

</details>

---

<details>
<summary>5. 如何在 Client Component 中调用 Server Action？</summary>

**答：**

Server Action 是定义在服务端的函数，可在客户端调用：

```ts
// app/actions.ts
'use server';
export async function createPost(data: FormData) {
  'use server';
  // 直接访问数据库
  await db.post.create({ data });
}
```

```tsx
// app/page.tsx (Client Component)
'use client';
import { createPost } from './actions';

export default function Form() {
  return (
    <form action={createPost}>
      <input name="title" />
      <button type="submit">发布</button>
    </form>
  );
}
```

✅ **优点**：免 API 路由，安全（自动 CSRF 保护），支持 FormData。

</details>

---

<details>
<summary>6. 如何实现动态路由？比如 /user/[id]</summary>

**答：**

使用文件夹命名：

```
app/
  user/
    [id]/
      page.tsx
```

```tsx
// app/user/[id]/page.tsx
export default function Page({ params }: { params: { id: string } }) {
  return <div>用户 ID: {params.id}</div>;
}
```

✅ 支持嵌套、可选段（`[[slug]]`）。

</details>

---

<details>
<summary>7. 如何获取搜索参数（query params）？</summary>

**答：**

使用 `useSearchParams`（Client）或 `pageProps.searchParams`（Server）：

```tsx
// Client Component
'use client';
import { useSearchParams } from 'next/navigation';

export default function Page() {
  const searchParams = useSearchParams();
  const q = searchParams.get('q');
  return <div>搜索: {q}</div>;
}
```

```tsx
// Server Component
export default function Page({ searchParams }: { searchParams: { q?: string } }) {
  return <div>搜索: {searchParams.q}</div>;
}
```

</details>

---

<details>
<summary>8. 如何实现页面嵌套路由和布局（Layout）？</summary>

**答：**

创建 `layout.tsx` 文件，自动嵌套：

```
app/
  layout.tsx          ← 全局布局
  dashboard/
    layout.tsx        ← 仅 /dashboard 下生效
    page.tsx
```

```tsx
// app/dashboard/layout.tsx
export default function DashboardLayout({
  children,
}: { children: React.ReactNode }) {
  return (
    <div>
      <h1>Dashboard Layout</h1>
      {children}
    </div>
  );
}
```

✅ 支持 `template`（每次重新渲染）、`loading.tsx`、`error.tsx`。

</details>

---

<details>
<summary>9. 如何实现加载状态（Loading）？</summary>

**答：**

在目录下创建 `loading.tsx`：

```tsx
// app/blog/loading.tsx
export default function Loading() {
  return <p>加载中...</p>;
}
```

✅ 自动在 `page.tsx` 加载时显示，支持嵌套。

</details>

---

<details>
<summary>10. 如何处理错误边界（Error UI）？</summary>

**答：**

创建 `error.tsx` 文件（必须是 Client Component）：

```tsx
'use client';
export default function Error({ error }: { error: Error }) {
  return <div>出错了：{error.message}</div>;
}
```

✅ 可捕获其子组件的渲染错误。

</details>

---

<details>
<summary>11. 如何实现静态生成（SSG）和增量静态再生（ISR）？</summary>

**答：**

在 Server Component 中导出 `generateStaticParams` 和 `revalidate`：

```tsx
// 生成静态路径
export async function generateStaticParams() {
  const posts = await db.post.findMany();
  return posts.map((post) => ({ id: post.id }));
}

// ISR：每 60 秒重新生成
export const dynamic = 'force-dynamic'; // 或 'auto'
export const revalidate = 60;
```

✅ `revalidate` > 0 启用 ISR。

</details>

---

<details>
<summary>12. 如何禁用缓存，实现动态渲染？</summary>

**答：**

设置 `dynamic` 选项：

```ts
export const dynamic = 'force-dynamic'; // 总是动态
// 或
export const dynamic = 'auto'; // 默认，有 fetch 时缓存
```

也可使用 `cache: 'no-store'`：

```ts
fetch('/api/data', { cache: 'no-store' });
```

</details>

---

<details>
<summary>13. 如何使用 Turbopack？它比 Webpack 快多少？</summary>

**答：**

Turbopack 是 Next.js 13+ 的实验性打包器（基于 Rust），启动命令：

```bash
next dev --turbo
```

✅ **优势**：
- 启动速度提升 10x~70x（尤其大型项目）
- 按需编译（on-demand)
- 原生支持 TS、JSX、CSS Modules

⚠️ 注意：生产环境仍使用 Webpack（Turbopack 生产版仍在开发中）。

</details>

---

<details>
<summary>14. 如何在 Server Action 中上传文件？</summary>

**答：**

使用 `FormData` + Server Action：

```ts
'use server';
export async function uploadFile(formData: FormData) {
  const file = formData.get('file') as File;
  const bytes = await file.arrayBuffer();
  // 保存到磁盘或云存储
}
```

```tsx
<form action={uploadFile}>
  <input type="file" name="file" />
  <button>上传</button>
</form>
```

✅ 无需 API 路由，但大文件建议用专门服务（如 S3 + presigned URL）。

</details>

---

<details>
<summary>15. 如何实现身份认证（Auth）？推荐方案？</summary>

**答：**

推荐使用 **Auth.js（原 NextAuth.js）**：

```ts
// app/api/auth/[...nextauth]/route.ts
import NextAuth from 'next-auth';
import GoogleProvider from 'next-auth/providers/google';

const handler = NextAuth({
  providers: [GoogleProvider({ clientId: '', clientSecret: '' })],
  pages: { signIn: '/login' },
});

export { handler as GET, handler as POST };
```

✅ 支持 OAuth、Credentials、Email 等多种方式。

</details>

---

<details>
<summary>16. 如何自定义 API 路由？</summary>

**答：**

在 `app/api/` 下创建路由处理程序（Route Handlers）：

```ts
// app/api/hello/route.ts
export async function GET(request: Request) {
  return Response.json({ message: 'Hello' });
}

export async function POST(request: Request) {
  const data = await request.json();
  return Response.json({ received: data });
}
```

✅ 替代旧的 `pages/api`，更贴近 Web API 标准。

</details>

---

<details>
<summary>17. 如何实现中间件（Middleware）？</summary>

**答：**

创建 `middleware.ts`：

```ts
// middleware.ts
import { NextRequest, NextFetchEvent } from 'next/server';

export function middleware(request: NextRequest) {
  const path = request.nextUrl.pathname;
  if (path === '/admin') {
    // 重定向或验证
    return Response.redirect(new URL('/login', request.url));
  }
}
```

✅ 可用于身份验证、A/B 测试、区域重定向等。

</details>

---

<details>
<summary>18. 如何优化图片？使用哪个组件？</summary>

**答：**

使用 `next/image`：

```tsx
import Image from 'next/image';

<Image
  src="/me.png"
  alt="me"
  width={300}
  height={300}
  priority
  placeholder="blur"
  blurDataURL="data:..."
/>
```

✅ 自动优化：懒加载、格式转换（WebP）、CDN 支持。

</details>

---

<details>
<summary>19. 如何实现国际化（i18n）路由？</summary>

**答：**

配置 `next.config.js`：

```js
// next.config.js
module.exports = {
  i18n: {
    locales: ['en', 'zh'],
    defaultLocale: 'zh',
  },
};
```

路径自动支持：`/en/about`、`/zh/about`

✅ 也可使用基于域名的国际化。

</details>

---

<details>
<summary>20. 如何部署 Next.js 应用？</summary>

**答：**

推荐平台：
- **Vercel**：官方团队开发，一键部署，完美支持 App Router、Server Actions
- **Netlify**、**AWS Amplify**、**Docker + Node.js 服务器**

生产构建命令：

```bash
next build
next start
```

✅ Vercel 零配置，支持边缘函数、ISR、缓存自动管理。

</details>

---

## ✅ 总结：Next.js 14 核心重点

| 类别 | 关键技术 |
|------|--------|
| 架构 | App Router、Server Components |
| 数据流 | Server Actions、`async` 组件 |
| 性能 | Turbopack（开发）、ISR、Streaming |
| 交互 | Client Components + `'use client'` |
| 部署 | Vercel、Edge Functions、Serverless |
| 生态 | Auth.js、next/image、next/font |

---

🎯 **高手建议**：
- 新项目一律使用 **App Router**
- 能用 **Server Component** 就不用 Client
- 用 **Server Actions** 替代部分 API 路由
- 开发用 **Turbopack**，生产用 Webpack（当前）
- 部署首选 **Vercel**

---

需要 **PDF 打包版、面试题合集、项目模板**，欢迎继续提问！


---

当然可以！以下是一套 **从新手到高手的前端开发必备 100 个工程实战练习题**，**聚焦现代前端工程化、TypeScript、React、Next.js、构建部署、性能优化与 AI 集成**，每道题均附带 **详细答案与代码示例**，采用 `<details><summary>` 折叠格式，便于学习与复习。

> ✅ 适用人群：前端初学者 → 中高级开发者  
> ✅ 技术栈：TypeScript + React + Next.js 14 + Tailwind CSS + Zod + TanStack Query + Git + Vercel  
> ✅ 目标：掌握真实项目中所需的 **工程能力、架构思维与最佳实践**

---

## 📘 第一阶段：基础工程能力（1-30）—— 新手入门

<details>
<summary>1. 初始化一个 Next.js 14 项目，使用 App Router 和 TypeScript。</summary>

```bash
npx create-next-app@latest my-app \
  --use-turbo \
  --typescript \
  --tailwind \
  --app \
  --src-dir
```

✅ 自动生成 `app/page.tsx`、`tsconfig.json`、`tailwind.config.ts` 等。

</details>

---

<details>
<summary>2. 创建一个可复用的 Button 组件，支持 variant（primary / secondary）和 loading 状态。</summary>

```tsx
// components/Button.tsx
export function Button({
  children,
  variant = 'primary',
  loading = false,
  disabled,
  ...props
}: {
  children: React.ReactNode;
  variant?: 'primary' | 'secondary';
  loading?: boolean;
  disabled?: boolean;
} & React.ButtonHTMLAttributes<HTMLButtonElement>) {
  const base = 'px-4 py-2 rounded font-medium flex items-center gap-2';
  const variants = {
    primary: 'bg-blue-600 text-white hover:bg-blue-700',
    secondary: 'bg-gray-200 text-gray-800 hover:bg-gray-300',
  };

  return (
    <button
      className={`${base} ${variants[variant]} ${loading ? 'opacity-70' : ''}`}
      disabled={disabled || loading}
      {...props}
    >
      {loading && <span className="loading"></span>}
      {children}
    </button>
  );
}
```

</details>

---

<details>
<summary>3. 使用 Zod 定义用户注册表单的校验 schema。</summary>

```ts
// lib/schema.ts
import { z } from 'zod';

export const registerSchema = z.object({
  name: z.string().min(2, '姓名至少2字'),
  email: z.string().email('邮箱格式错误'),
  password: z.string().min(6, '密码至少6位'),
  confirmPassword: z.string(),
}).refine(data => data.password === data.confirmPassword, {
  message: "密码不一致",
  path: ["confirmPassword"],
});

export type RegisterForm = z.infer<typeof registerSchema>;
```

</details>

---

<details>
<summary>4. 使用 React Hook Form + Zod 实现表单校验。</summary>

```tsx
// components/RegisterForm.tsx
import { useForm } from 'react-hook-form';
import { zodResolver } from '@hookform/resolvers/zod';
import { registerSchema, RegisterForm } from '@/lib/schema';

export function RegisterForm() {
  const { register, handleSubmit, formState: { errors } } = useForm<RegisterForm>({
    resolver: zodResolver(registerSchema),
  });

  const onSubmit = (data: RegisterForm) => {
    console.log(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register('name')} />
      {errors.name && <span>{errors.name.message}</span>}
      {/* 其他字段... */}
      <button type="submit">注册</button>
    </form>
  );
}
```

</details>

---

<details>
<summary>5. 在 Next.js 中创建 API 路由，接收注册请求并返回 JSON。</summary>

```ts
// app/api/auth/register/route.ts
import { NextRequest } from 'next/server';
import { registerSchema } from '@/lib/schema';

export async function POST(request: NextRequest) {
  const body = await request.json();
  const result = registerSchema.safeParse(body);

  if (!result.success) {
    return Response.json(
      { error: result.error.flatten() },
      { status: 400 }
    );
  }

  // 模拟保存
  return Response.json({ message: '注册成功' }, { status: 201 });
}
```

</details>

---

<details>
<summary>6. 使用 Tailwind 实现一个响应式导航栏（移动端汉堡菜单）。</summary>

```tsx
// components/Navbar.tsx
'use client';
import { useState } from 'react';

export function Navbar() {
  const [open, setOpen] = useState(false);
  return (
    <nav className="bg-white shadow">
      <div className="max-w-6xl mx-auto px-4">
        <div className="flex justify-between h-16">
          <div className="flex items-center">Logo</div>
          <div className="md:hidden">
            <button onClick={() => setOpen(!open)}>☰</button>
          </div>
          <div className={`md:flex ${open ? 'block' : 'hidden'}`}>
            <a href="/" className="p-2">首页</a>
            <a href="/about" className="p-2">关于</a>
          </div>
        </div>
      </div>
    </nav>
  );
}
```

</details>

---

<details>
<summary>7. 配置 ESLint + Prettier，实现代码规范统一。</summary>

```bash
npm install --save-dev eslint prettier eslint-config-next eslint-config-prettier
```

`.eslintrc.json`：
```json
{
  "extends": ["next/core-web-vitals", "prettier"],
  "rules": {
    "@next/next/no-html-link-for-pages": "off"
  }
}
```

`.prettierrc`：
```json
{
  "semi": true,
  "trailingComma": "es5",
  "singleQuote": true,
  "printWidth": 80
}
```

</details>

---

<details>
<summary>8. 使用 Git 初始化项目，提交初始代码并推送到 GitHub。</summary>

```bash
git init
git add .
git commit -m "feat: init project"
git branch -M main
git remote add origin https://github.com/yourname/my-app.git
git push -u origin main
```

</details>

---

<details>
<summary>9. 部署 Next.js 项目到 Vercel。</summary>

1. 登录 [vercel.com](https://vercel.com)
2. 导入 GitHub 仓库
3. 自动检测为 Next.js，点击 Deploy
4. 完成，获得 `my-app.vercel.app`

✅ 支持自动 CI/CD、环境变量、自定义域名。

</details>

---

<details>
<summary>10. 创建一个 loading.tsx，为博客页面提供加载状态。</summary>

```tsx
// app/blog/loading.tsx
export default function Loading() {
  return (
    <div className="flex items-center justify-center h-64">
      <p>加载中...</p>
    </div>
  );
}
```

✅ 自动在 `page.tsx` 加载时显示。

</details>

---

（继续中……以下为节选）

---

## 🧠 第二阶段：进阶工程能力（31-70）—— 中级实战

<details>
<summary>31. 使用 TanStack Query 获取用户列表，并实现缓存和轮询。</summary>

```ts
// app/hooks/useUsers.ts
import { useQuery } from '@tanstack/react-query';

async function fetchUsers() {
  const res = await fetch('/api/users');
  return res.json();
}

export function useUsers() {
  return useQuery({
    queryKey: ['users'],
    queryFn: fetchUsers,
    refetchInterval: 30000, // 每30秒轮询
  });
}
```

</details>

---

<details>
<summary>50. 使用 Server Actions 实现文章发布功能，无需 API 路由。</summary>

```ts
// app/actions.ts
'use server';
import { revalidatePath } from 'next/cache';

export async function createPost(formData: FormData) {
  'use server';
  const title = formData.get('title') as string;
  await db.post.create({ data: { title } });
  revalidatePath('/posts');
}
```

```tsx
// app/new/page.tsx
'use client';
export default function NewPost() {
  return (
    <form action={createPost}>
      <input name="title" placeholder="标题" />
      <button type="submit">发布</button>
    </form>
  );
}
```

</details>

---

<details>
<summary>60. 实现暗黑模式切换，使用 CSS 变量和 localStorage。</summary>

```css
/* globals.css */
:root {
  --bg: white;
  --text: black;
}

.dark {
  --bg: #1a1a1a;
  --text: #eee;
}

body {
  background: var(--bg);
  color: var(--text);
  transition: all 0.3s;
}
```

```tsx
'use client';
export function ThemeToggle() {
  const [dark, setDark] = useState(false);
  useEffect(() => {
    if (localStorage.theme === 'dark') setDark(true);
  }, []);
  useEffect(() => {
    document.documentElement.classList.toggle('dark', dark);
    localStorage.theme = dark ? 'dark' : 'light';
  }, [dark]);
  return <button onClick={() => setDark(!dark)}>切换主题</button>;
}
```

</details>

---

## 🚀 第三阶段：高手工程能力（71-100）—— 架构与 AI

<details>
<summary>75. 设计一个支持 AI 助手的聊天界面，使用 Server Actions 调用 LLM。</summary>

```ts
// app/actions.ts
'use server';
export async function askAI(prompt: string) {
  const res = await fetch('https://api.openai.com/v1/completions', {
    method: 'POST',
    headers: {
      'Authorization': `Bearer ${process.env.OPENAI_KEY}`,
      'Content-Type': 'application/json',
    },
    body: JSON.stringify({
      model: 'text-davinci-003',
      prompt,
      max_tokens: 200,
    }),
  });
  const data = await res.json();
  return data.choices[0].text;
}
```

```tsx
// app/ai/page.tsx
'use client';
const [input, setInput] = useState('');
const [reply, setReply] = useState('');

const handleSubmit = async () => {
  const res = await askAI(input);
  setReply(res);
};
```

</details>

---

<details>
<summary>90. 实现 CI/CD 流程：Push 到 main 触发测试 + 构建 + 部署到 Vercel。</summary>

使用 GitHub Actions：

```yaml
# .github/workflows/deploy.yml
name: Deploy
on: [push]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: pnpm/action-setup@v3
      - run: pnpm install
      - run: pnpm build
      - uses: amondnet/vercel-action@v2
        with:
          project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          token: ${{ secrets.VERCEL_TOKEN }}
```

</details>

---

<details>
<summary>100. 如何设计一个可扩展的前端架构？列出核心原则。</summary>

✅ **现代前端架构原则**：

1. **模块化**：按功能拆分 `features/`, `shared/`, `entities/`
2. **类型优先**：TS + Zod 保证数据安全
3. **服务端优先**：Server Components + Server Actions 减少客户端负担
4. **自动化**：ESLint + Prettier + Husky + CI/CD
5. **性能优先**：ISR、Streaming、Code Splitting
6. **可观测性**：日志、错误监控（Sentry）、埋点
7. **AI 集成**：智能生成、自动摘要、自然语言交互

📌 示例结构：

```
src/
  features/auth/
  features/post/
  entities/user/
  shared/ui/
  lib/api/
  lib/schema/
```

</details>

---

## 📦 附：完整 100 题目录（可扩展）

| 范围 | 题号 |
|------|------|
| 项目初始化 | 1-10 |
| 组件开发 | 11-20 |
| 表单处理 | 21-30 |
| 数据请求 | 31-40 |
| 状态管理 | 41-50 |
| 路由与导航 | 51-60 |
| 样式与主题 | 61-70 |
| 安全与部署 | 71-80 |
| 性能优化 | 81-90 |
| 架构与 AI | 91-100 |

---

✅ **获取完整版方式**：

回复以下任一需求，我可为你生成：
- 📄 PDF 版（带目录、可打印）
- 💾 Markdown 文件（可导入 Obsidian）
- 🧩 Next.js 项目模板（含所有练习）
- 📚 面试高频题 Top 50 精简版

> 🔥 掌握这 100 个练习，你将具备独立开发和架构现代前端应用的 **全栈工程能力**。