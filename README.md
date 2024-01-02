# TOML Parser / Writer

This library provides a pure stanza implementation of a [TOML](https://toml.io) format parser/writer.

# Using this library

The easiest way to use this library is:

1.  Use [slm](https://github.com/StanzaOrg/slm) to manage dependencies in your [stanza](https://lbstanza.org) project.
    1.  slm add -git StanzaOrg/slm
2.  Use a git submodule and manage dependencies manually.

## Example:

```stanza
defn get-name-version (path:String) -> [String, String] :
  val tab = table $ parse-file(path)
  val name = tab["name"] as String
  val version = tab["version"] as String
  [name, version]
```

# Limitations

This library currently does **not** support [inline arrays](https://toml.io/en/v1.0.0#array).

```
# Not Supported:
args = [ "apple", "orange", "kiwi"]
```

It also does **not** support [RFC 3339 date-time](https://toml.io/en/v1.0.0#offset-date-time).

```
created = 1979-05-27T07:32:00
```

# Running the tests

1.  Have [stanza](https://lbstanza.org/) installed and available on your `$PATH`.
2.  Have [slm](https://github.com/StanzaOrg/slm) installed and available on your `$PATH`
3.  You will also need `gcc` available on your `$PATH`

Run:

```
$> slm build test
$> ./toml-test
```