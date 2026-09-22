```bash
src=$(mktemp -d)
git clone --depth 1 https://github.com/Pipelex/pipelex-method-apps.git "$src"
mkdir -p my-app && cp -R "$src/webapp-js/." my-app/
cd my-app && git init

export PIPELEX_API_KEY=plx_sk_...
make create METHOD=path/to/my_method.mthds
make dev
```

The app calls Pipelex from its own server code, so it needs a key of its own — create one in your console at [app.pipelex.com](https://app.pipelex.com). `METHOD` is a `.mthds` file, a directory of them, a method id from your catalog (`mt_…`), or a published address. The form and the result view are rendered from the method's own contract, so adding a method writes no form fields.
