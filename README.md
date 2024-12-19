# repro-consola-import

A minimal reproduction of being unable to import the `consola` package under the
node16 module resolution mode.

To reproduce the issue:

```console
$ git clone https://github.com/bryan-hoang/repro-consola-import.git
$ cd repro-consola-import
$ pnpm install
$ pnpm run repro
> repro-consola-import@ repro <...>/repro-consola-import
> tsc --noEmit

index.ts:1:21 - error TS1479: The current file is a CommonJS module whose imports will produce 'require' calls; however, the referenced file is an ECMAScript module and cannot be imported with 'require'. Consider writing a dynamic 'import("consola")' call instead.
  To convert this file to an ECMAScript module, change its file extension to '.mts', or add the field `"type": "module"` to '<...>/repro-consola-import/package.json'.

1 import consola from 'consola';
                      ~~~~~~~~~

index.ts:2:24 - error TS1479: The current file is a CommonJS module whose imports will produce 'require' calls; however, the referenced file is an ECMAScript module and cannot be imported with 'require'. Consider writing a dynamic 'import("consola/utils")' call instead.
  To convert this file to an ECMAScript module, change its file extension to '.mts', or add the field `"type": "module"` to '<...>/repro-consola-import/package.json'.

2 import { colors } from 'consola/utils';
                         ~~~~~~~~~~~~~~~


Found 2 errors in the same file, starting at: index.ts:1

 ELIFECYCLE  Command failed with exit code 2.
```
