# lpyth

VS Code extension for LPython Language.

![demo_lpyth](https://user-images.githubusercontent.com/68434944/181516697-eadb63e5-cbf1-437d-bb5c-f070671dff32.gif)

There are no pre-packaged versions of this extension, but will be packaging the extension to VS Code market place very soon. 

## Key Features

1. Linting: highlights errors and warnings in your LPython code which helps you to identify and correct programming errors.
2. Document Symbol Lookup: You can navigate symbols inside a file with `Ctrl + Shift + O`. By typing `:` the symbols are grouped by category. Press Up or Down and navigate to the place you want.

## Language Server

- The Language Server is written in TypeScript, which uses [Microsoft’s official language server module](https://github.com/microsoft/vscode-languageserver-node). 
- Communication between the language server and LPython Compiler is done with 
    ```bash
        const stdout = await runCompiler(text, "<flags>", settings); `
    ```

## Usage

Compile lpython with LSP flag on (Refer to [lpython documentation](https://github.com/lcompilers/lpython#compile-lpython)):

```bash
conda activate lp # or use your environment name here
cmake -DCMAKE_BUILD_TYPE=Debug -DWITH_LLVM=yes -DWITH_STACKTRACE=yes -DWITH_LFORTRAN_BINARY_MODFILES=no -DWITH_LSP=yes .
cmake --build . -j16
```

1. Clone https://github.com/ankitaS11/lpyth
2. Go to: `lpyth/src/server.ts` file and replace the binary path of LPython in line number 103 to your binary path.
3. Go to: `lpyth/package.json` file and replace the binary path of LPython in line number 60 to your binary path.
4. Build the extension:

```bash
cd lpyth && npm install && npm run compile
```

Open VSCode in the extension folder (`code editor/vscode/lsp-sample/`) and run `ctrl + shift + D`, click on “Run and Debug” and choose VSCode Extension Development, and test the extension. :)

To package the extension, you can do:

```bash
npm install -g vsce
vsce package
```

This will generate a .vsix file in your `lpyth` folder, which can then be imported as an extension. You can go to extensions in VSCode, click on `...` on the top right, click on “Install from VSIX” and select the VSIX, and done (may require a reload). The extension has now been installed.
