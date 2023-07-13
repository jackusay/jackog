---
published: true
---
## A New Post


Error: Could not search on Google: Request failed with status code 429 #14

https://github.com/LuanRT/google-this/issues/14

I have the same problem.
browser can get the results, but this library get - Request failed with status code 429

```
C:\Users\xxx\a7\node_modules\googlethis\lib\core\main.js:70
    throw new Utils.SearchError('Could not execute search', {
          ^

SearchError: Could not execute search
    at Object.search (C:\Users\xxx\a7\node_modules\googlethis\lib\core\main.js:70:11)
    at process.processTicksAndRejections (node:internal/process/task_queues:95:5)
    at async file:///C:/Users/xxx/a7/aa.mjs:18:18 {
  info: { status_code: 0, message: 'Request failed with status code 429' },
  date: 2023-07-13T00:55:36.790Z,
  version: '1.7.1'
}
```
