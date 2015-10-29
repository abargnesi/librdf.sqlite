# Testing Load and Query of Large Triple datasets

## Summary

Write a C main function that will log and time loading and querying of triples using librdf.sqlite.

Inputs: RDF URI (to load), Store name (sqlite, http://purl.mro.name/rdf/sqlite/)
Output: Log and timing reported to console

## Tasks

1. Modular loading of "http://purl.mro.name/rdf/sqlite/" storage with stock redland 1.0.17.

```bash
  # Copy header to ~/projects/tools/redland/dist/include/.
  $ cp rdf_storage_sqlite_mro.h ~/projects/tools/redland/dist/include/

  # Compile shared library for "http://purl.mro.name/rdf/sqlite/".
  $ LD_LIBRARY_PATH=/home/tony/projects/tools/redland/dist/lib/ gcc -c -fPIC -I ~/projects/tools/redland/dist/include/ -I /home/tony/projects/tools/redland/dist/include/raptor2/ -I /home/tony/projects/tools/redland/dist/include/rasqal/ rdf_storage_sqlite_mro.c 

  # Link to rdf/sqlite3.
  $ LD_LIBRARY_PATH=/home/tony/projects/tools/redland/dist/lib/ gcc -shared -lrdf -lsqlite3 -o rdf_storage_sqlite_mro.so rdf_storage_sqlite_mro.o

  # Copy to librdf storage backend dir.
  $ cp rdf_storage_sqlite_mro.so ~/projects/tools/redland/dist/lib/redland/

  # Compile/Link main loader.
  $ LD_LIBRARY_PATH="/home/tony/projects/tools/redland/dist/lib/" gcc -I ~/projects/tools/redland/dist/include/ -I /home/tony/projects/tools/redland/dist/include/raptor2/ -I /home/tony/projects/tools/redland/dist/include/rasqal/ demo/loader.c -lrdf -lsqlite3 -L/home/tony/projects/tools/redland/dist/lib/redland -lrdf_storage_sqlite_mro -o loader

  # Run with "sqlite" backend.
  LD_LIBRARY_PATH="/home/tony/projects/tools/redland/dist/lib/:/home/tony/projects/tools/redland/dist/lib/redland" ./loader "file://$(pwd)/file.nt" "sqlite"

  # Run with "http://purl.mro.name/rdf/sqlite/" backend.
  LD_LIBRARY_PATH="/home/tony/projects/tools/redland/dist/lib/:/home/tony/projects/tools/redland/dist/lib/redland" ./loader "file://$(pwd)/file.nt" "http://purl.mro.name/rdf/sqlite/"
```

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
