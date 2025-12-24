# Detypify External

- Requires [Git LFS](https://git-lfs.com/)
- Licenses locate in [vendors](./vendors/) folder
- Check [detypify](https://github.com/QuarticCat/detypify) repo for detailed usage

## Where Are They From

### Training Dataset

**Contains training dataset from detexify.**

Source: https://github.com/kirel/detexify-data

```console
$ # TODO: Download detexify.sql.gz & symbols.json here.
$ gunzip -c detexify.sql.gz | psql detypify
$ psql detypify -qAtXc 'SELECT json_agg(json_build_array(key, strokes)) FROM samples' -o detexify.json
$ rm detexify.sql.gz
```

### Typst Symbol Page

**Contains Typst symbol information.**

Source: https://typst.app/docs/reference/symbols/sym

```console
$ curl https://typst.app/docs/reference/symbols/sym/ -o typ_sym.html
```

### Symbol Font

**The font used for symbols on the website.**

Source: https://ctan.org/pkg/newcomputermodern

```console
$ curl https://ctan.math.washington.edu/tex-archive/fonts/newcomputermodern.zip -O
$ unzip -j newcomputermodern.zip '**/NewCMMath-Regular.otf'
$ rm newcomputermodern.zip
```
