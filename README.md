# Reproduction for [npm/cli#4512](https://github.com/npm/cli/issues/4512)

> Reproduction for a possible bug preventing dependency hoisting in npm workspaces

1. Setup

   ```sh
   # Clone this repository
   git clone https://github.com/loilo/repro-npm-workspaces-hoisting.git
   
   # cd into the cloned folder
   cd repro-npm-workspaces-hoisting
   ```

2. Verify the reported behavior:

   1. Install dependencies:

      ```sh
      npm install
      ```

   2. The `jest` dependency will not be installed in the project root but in the individual workspace folders.

3. Crosscheck:

   1. Remove installed dependencies and lock file:

      ```sh
      git clean -d -f
      ```
   
   2. Remove or rename the `workspaces/jest` folder.

      ```sh
      mv workspaces/jest workspaces/quest
      ```

   3. Install dependencies again:

      ```sh
      npm install
      ```

   4. All dependencies are properly installed in the project root.