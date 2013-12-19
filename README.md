JSONUtil
========

JSON parser/printer for VDM-SL

JSON <-> VDM mappings
* JSON = seq of char;
* STRING = seq of char;
* ARRAY = seq of VALUE;
* OBJECT = map STRING to VALUE;
* NUMBER = real;
* BOOL = bool;
* VALUE = [ STRING | ARRAY | OBJECT | NUMBER | BOOL ];

exports the following functions

* parseJSON : JSON -> bool * VALUE;
  - parses the given JSON string into a VDM value.
  - This function permits extra data after a valid JSON portion.
* strictParseJSON : JSON -> bool * VALUE;
  - parses the given JSON string into a VDM value.
  - This function does NOT permit extra data after a valid JSON portion.
* printJSON : VALUE -> JSON;
  - prints the VALUE values into JSON format.
