# learn-scm
Aprenda a criar um SIMPLES SCM (Source Control Management). Bem que poderia ser SGCCF (Sistema de Gerenciamento e Controle de Código Fonte)

# ideia
COMMIT:
+ `id`            SHA-1/SHA-2 Identificator (ID)
+ `parent_id`     COMMIT parent ID
+ `author`        Author information (name <email>)
+ `datetime`      Timestamp date and time information
+ `description`   User description

POINTER:
+ `name`          Pointer name (alias for COMMIT)
+ `commit_id`     COMMIT ID

COMMIT_OBJECT:
+ `commit_id`      COMMIT ID
+ `object_id`      OBJECT ID

OBJECT:
+ `id`            OBJECT ID
+ `type`          Object type (BLOB or NODE )
+ `name`          Object name
+ `node_id`       NODE ID
+ `blob_id`       BLOB ID
  > Never $node_id and $blob_id simultaneously filled
  > Never $node_id and $blob_id simultaneously empty

NODE:
+ `id`            NODE ID
+ `author`        Author of the node change
+ `datetime`      Timestamp date and time information

BLOB:
+ `id`            BLOB ID
+ `type`          ${RESERVED = (TEXT or BINARY)}
+ `author`        Author of the blob change
+ `datetime`      Timestamp date and time information
+ `content`       Blog content (diff)

```
+--------+                   +---------------+                   +--------+
| COMMIT | [1]-----[0..*]-<< | COMMIT_OBJECT | >>-[0..*]-----[1] | OBJECT |
+--------+                   +---------------+                   +--------+
   [1]                                                            [1]  [1]
    |                                                  	           |    |
    |                                                              |    |
 [0..*]                                                       [0..1]    [0..1]
    \                                                           /         \
    /\                                                         /\         /\
+---------+                                               +------+        +------+
| POINTER |                                               | NODE |        | BLOB |
+---------+                                               +------+        +------+
```
