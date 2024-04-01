# Detypify Data

- Requires [Git LFS](https://git-lfs.com/)
- Licenses locates in [vendors](./vendors/) folder
- Check [detypify](https://github.com/QuarticCat/detypify) repo for detailed usage

## Where Are They From

### Training Data

**Contains original training data of detexify**

1. Download `detexify.sql.gz` and `symbols.json` from [detexify-data](https://github.com/kirel/detexify-data)

1. Convert training data to JSON (so that others don't have to host a PostgreSQL database to bootstrap)

    ```console
    $ gunzip -c detexify.sql.gz | psql detypify
    $ psql detypify -qAtXc 'SELECT json_agg(json_build_array(key, strokes)) FROM samples' -o detexify.json
    ```

### Symbol Mapping

**Contains mapping from LaTeX symbols to Typst symbols**

1. Clone [mitex](https://github.com/mitex-rs/mitex) and build `mitex-spec-gen`

    ```console
    $ git clone https://github.com/mitex-rs/mitex
    $ cd mitex
    $ cargo build --package=mitex-spec-gen
    ```

1. Move `target/mitex-artifacts/spec/default.json` here

### Typst Symbol Page

**Contains information about Typst symbols**

1. Access https://typst.app/docs/reference/symbols/sym/ in your browser

1. Right click -> Save as -> `typ_sym.html`

### Symbol Font

**Used to present symbols on the website**

1. Download *NewComputerModern* from [CTAN](https://ctan.org/pkg/newcomputermodern?lang=en)

1. Extract and move `NewCMMath-Regular.otf` here
