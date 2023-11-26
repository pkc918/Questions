> 使用 transformIndxHtml 方法替换 index.html 中的字符

``` ts
import { defineConfig } from "vite";

const htmlPlugin = () => {
  return {
    name: "script-transform",
    transformIndexHtml(html: string) {
      const hash = Date.now();
      return html
        .replace(".js", ".js?v=" + hash)
        .replace(".css", ".css?v=" + hash);
    },
  };
};

// https://vitejs.dev/config/
export default defineConfig(() => {
    plugins: [
      htmlPlugin(),
    ],
});
```