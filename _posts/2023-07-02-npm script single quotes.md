---
published: true
---
package.json:

```json
  "devDependencies": {},
  "scripts": {
    "speed": "hyperfine --runs 10 'bash build.bash'"
  },
```

error
```
$ npm run speed

> web@1.0.0 speed C:\Users\eight\Documents\GitHub\xxx
> hyperfine --runs 10 'bash ./build.bash'

 + Measuring shell spawning time  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ ETA 00:00:00 - Measuring shell spawning time  ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ ETA 00:00:00 x Measuring shell spawning time  ██████████████████████░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ ETA 00:00:00 | Measuring shell spawning time  ████████████████████████████████████████████░░░░░░░░░░░░░░░░░░░░░░░░░░░ ETA 00:00:00 + Measuring shell spawning time  ████████████████████████████████████████████████████████████████████░░░ ETA 00:00:00Benchmark 1: 'bash
 + Initial time measurement       ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ ETA 00:00:00 - Initial time measurement       ░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░ ETA 00:00:00Error: Command terminated with non-zero exit code: 1. Use the '-i'/'--ignore-failure' option if you want to ignore this. Alternatively, use the '--show-output' option to debug what went wrong.
npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! web@1.0.0 speed: `hyperfine --runs 10 'bash ./build.bash'`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the web@1.0.0 speed script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.

npm ERR! A complete log of this run can be found in:
npm ERR!     C:\Users\eight\AppData\Roaming\npm-cache\_logs\2023-07-02T04_31_17_747Z-debug.log
```

solution:
The issue was from the single quote ' being converted to "'" by npm when the arguments are forwarded, the solution was to replace them with double quotes like below.
  https://stackoverflow.com/questions/37500744/how-to-properly-run-a-npm-script-with-arguments