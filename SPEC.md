# Spec

We are big users of [DuckDB](https://duckdb.org/). Often we are generating embedding vectors to use for document similarity search or whatever AI feature d'jour strikes our fancy. It would be really convenient to be able to generate embedding vectors directly within the database. Something like this:

```sql
SELECT embed_text('We are the Knights Who Say... Nee!', 'CompendiumLabs/bge-large-en-v1.5-gguf');
┌──────────────────────────────────────────────────────────────────────────────┐
│                                  embedding                                   │
│                                   double[]                                   │
├──────────────────────────────────────────────────────────────────────────────┤
│ [0.40875935554504395, -0.3277415931224823, -0.4828256368637085, 0.45170360…  │
└──────────────────────────────────────────────────────────────────────────────┘
```

## Deliverables
- DuckDB extension that can be installed on a Linux and OS X build of DuckDB v1.2+.
- Extension should provide `embed_text(text, model)` function that will make an embedding vector of whatever length is specified by the model.
- Some way to pull and store models. This can either be automatic (if model not available when calling `embed_text` it will automatically be downloaded) or explicit (another function like `SELECT pull_model(model)`).
- README with steps to build, distribute, and install the extension.

## Test
TODO but some sort of checksum for a test vector.
