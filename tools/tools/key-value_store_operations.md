# Key-Value Store Operations

## put

To put a record in the database, use the put command:
>```ascli put <ns> <set> <key> <record>```

The <ns> is the namespace for the record being written.

The <set> is the set for the record being written.

The <key> is the key for the record being written. It can be either an integer or string.

The <record> is a JSON object representing the record to be written. The JSON object's keys are the bin names and the value are bin values.

The values will be either an Integer, String, List, or Map. The List is encoded as a JSON Array. The Map is encoded as a JSON Object.

Success is indicated by a "0" exit code. Any other exit code indicates a failure.

###Example:

```$ ascli put test test test '{"a": "A", "b": 1, "c": [1,2,3], "d": {"x": 4}}'
$ if [ $? == 0 ]; then echo "success"; else echo "failure"; fi;
success```


## get

To get a record from the database, use the get comamand:

>```ascli get <ns> <set> <key>```

###Example:

```$ ascli get test test test
{"a": "A", "b": 1, "c": [1,2,3], "d": {"x": 4}}```

## exists

>```ascli exists <ns> <set> <key>```

### Example:

>```$ ascli exists test test test```

## remove

>```ascli remove <ns> <set> <key>```
