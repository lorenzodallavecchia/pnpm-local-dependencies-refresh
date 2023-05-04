# Local Dependencies Refresh Bug



## Scenario 1 - Peer Dependencies

1. `pnpm i` 
   - `@angular/core@13.0.0` is installed.
2. In `local-package/package.json` , change Angular version to `14.0.0`.
3. `pnpm i`
   - The resolution step is skipped, although the local package changed.
     "Lockfile is up to date, resolution step is skipped"
   - The installed `@angular/core` is not updated.



## Scenario 2 - Files

1. `pnpm i` 
   - In `node_modules\.pnpm\node_modules\local-package` contains only the `index.js` file (correctly).
2. In `local-package/package.json` , add `other.js` for the `files` list.
3. `pnpm i`
   - The resolution step is skipped, although the local package changed.
     "Lockfile is up to date, resolution step is skipped"
   - In `node_modules\.pnpm\node_modules\local-package` the `other.js` file is not present.