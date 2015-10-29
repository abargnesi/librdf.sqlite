# Testing Load and Query of Large Triple datasets

## Summary

Write a C main function that will log and time loading and querying of triples using librdf.sqlite.

Inputs: RDF URI (to load), Store name (sqlite, http://purl.mro.name/rdf/sqlite/)
Output: Log and timing reported to console

## Tasks

1. Modular loading of "http://purl.mro.name/rdf/sqlite/" storage with stock redland 1.0.17.
2. Add loading of RDF URI to the stated storage backend. Log and time process.
3. (optional) Create C macros that make it trivial to create librdf_statement patterns for query.
4. Query against loaded model given subject, predicate, object, subject-predicate, subject-predicate-object.

## Long-term goal

Create check tests based on assertions in C main function. Integrate these with librdf.sqlite for regression purposes.

## Branch

Changes are being made to the *feature/issue11* branch.

## GitHub Issue

Upstream this is located [here](https://github.com/mro/librdf.sqlite/issues/11). [Comment](https://github.com/mro/librdf.sqlite/issues/11#issuecomment-151988824) spurred this exploration.

## Resources

Example load and query main function in librdf. [Source](https://github.com/dajobe/librdf/blob/master/examples/example1.c)
