# Known limitations

MeiliSearch has known limitations, some of which may be addressed in future versions

## Design limitations

### Database size

Default database maximum size is 100GiB.
MeiliSearch uses LMDB under the hood as the storage engine. On launch, LMDB need to know the size that it can allocate on disk. This space will be reserved on disk for LMDB, thus MeiliSearch. This space will also be allocated as virtual memory, which is different from the real memory. You can read more [about storage](/resources/about_storage.md).
You can modify this default limit using the options `--max-mdb-size` & `--max-udb-size` as described in the [configuration guide](/guides/advanced_guides/configuration.md#max-mdb-size).

### Number of indexes

You can create up to 200 indexes in MeiliSearch. When using LMDB, MeiliSearch have to specify a number of databases that must stay low for performance reasons.

### Maximum words per attribute

A maximum of  1000 words par attribute can be indexed. This limit is enforced for relevancy reasons. The more words there are in a given attribute, the less relevant will be the search queries.
If you put more than 1000 words in one attribute, only the first 1000 will be indexed.

## Other limitations

### Payload size

The default limit for the payload size is around 10MB. [This limit can be modified](/guides/advanced_guides/configuration.md#options).
