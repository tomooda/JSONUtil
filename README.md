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

parseJSON : JSON -> bool * VALUE;
    parses the given JSON string into a VDM value.
    This function permits extra data after a valid JSON portion.
    examples
        parseJSON("[1, {\"key\":\"value\"}]") ==> mk_(true, [1, {"key"|->"value}])
        parseJSON("[true, false, null]") ==> mk_(true, [true, false, nil])
        parseJSON("null") ==> mk_(true, nil)
        parseJSON("BAD JSON") ==> mk_(false, nil)
        parseJSON("[true, false, null] []") ==> mk_(true, [true, false, nil])
        parseJSON("[true, false, null] BAG JSON") ==> mk_(true, [true, false, nil])
        
strictParseJSON : JSON -> bool * VALUE;
    parses the given JSON string into a VDM value.
    This function does NOT permit extra data after a valid JSON portion.
    examples
        parseJSON("[1, {\"key\":\"value\"}]") ==> mk_(true, [1, {"key"|->"value}])
        parseJSON("[true, false, null]") ==> mk_(true, [true, false, nil])
        parseJSON("null") ==> mk_(true, nil)
        parseJSON("BAD JSON") ==> mk_(false, nil)
        parseJSON("[true, false, null] []") ==> mk_(false, nil)
        parseJSON("[true, false, null] BAG JSON") ==> mk_(false, nil)
printJSON : VALUE -> JSON;
    prints the VALUE values into JSON format.
