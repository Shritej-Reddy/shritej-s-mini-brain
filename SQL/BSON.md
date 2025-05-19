BSON is a binary encoded Javascript Object Notation (JSON)—a textual object notation widely used to transmit and store data across web based applications. JSON is easier to understand as it is human-readable, but compared to BSON, it supports fewer data types. BSON encodes type and length information, too, making it easier for machines to parse.

BSON stands for Binary Javascript Object Notation. It is a bin­ary-en­coded seri­al­iz­a­tion of JSON documents. BSON has been extended to add some optional non-JSON-native data types, like dates and binary data.

## How is BSON Different from JSON?

|                   | **JSON**                                                                                                       | **BSON**                                                                                                |
| ----------------- | -------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Type              | JSON files are written in text format.                                                                         | BSON files are written in binary.                                                                       |
| Speed             | JSON is fast to read but slower to build.                                                                      | BSON is slow to read but faster to build and scan.                                                      |
| Space             | JSON data is slightly smaller in byte size.                                                                    | BSON data is slightly larger in byte size.                                                              |
| Encode and Decode | We can send JSON through APIs without encoding and decoding.                                                   | BSON files are encoded before storing and decoded before displaying.                                    |
| Parse             | JSON is a human-readable format that doesn't require parsing.                                                  | BSON needs to be parsed as they are machine-generated and not human-readable.                           |
| Data Types        | JSON has a specific set of data types—string, boolean, number for numeric data types, array, object, and null. | Unlike JSON, BSON offers additional data types such as bindata for binary data, decimal128 for numeric. |
| Usage             | Used to send data through the network (mostly through APIs).                                                   | Databases use BSON to store data.                                                                       |

## Advantages of BSON

The fol­low­ing three char­ac­ter­ist­ics make BSON advantageous to use.

#### Lightweight and Traversable

BSON is lightweight: This makes it possible for a large amount of data to be stored in BSON file format. Additionally, BSON files are easily stored and sent through the network, making them perfect for storing and sending data.

#### Efficient

BSON was made to efficiently store space and scan: In a BSON document, large elements are prefixed with a length field. Documents in BSON use more space than JSON due to the length prefixes and explicit array indices, but thanks to those prefixes, we are able to scan and query much faster. The prefixes make it easy to compare and calculate directly on data, simplifying application code consumption.

### Handles Additional Data Types

Unlike in JSON, you can find data types such as Bindata, Minkey, Maxkey, Binary Data, ObjectID, Regular Expression, JavaScript, Decimal128, and Date for datetime in BSON. These data types are crucial when working with specialty programs.

For example, when working with [financial systems data](https://docs.mongodb.com/manual/tutorial/model-monetary-data/), you can use BSON’s Decimal128 for 128 bits of high precision decimal representation.

Many modern systems use binary-based floating-point arithmetic to represent exact decimal fractions through Float and double data types. These data types provide approximation but not the precise value. Using BSON in such cases gives you high precision.

Visit [BSON data types](https://www.mongodb.com/blog/post/the-top-12-bson-data-types-you-wont-find-in-json) to find the list of datatypes exclusive to BSON but not to JSON.