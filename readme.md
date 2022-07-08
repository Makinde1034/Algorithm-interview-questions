
// Person
var schema = {
  "id": "/SimplePerson",
  "type": "object",
  "properties": {
    "name": {"type": "string"},
    "address": {
  "id": "/SimpleAddress",
  "type": "object",
  "properties": {
    "lines": {
      "type": "array",
      "items": {"type": "string"}
    },
    "zip": {"type": "string"},
    "city": {"type": "string"},
    "country": {"type": "string"}
  },
  "required": ["country"]
     },
    "votes": {"type": "integer", "minimum": 1}
  }
};

var p = {
  "name": "Barack Obama",
  "address": {
    "lines": [ "1600 Pennsylvania Avenue Northwest" ],
    "zip": 340000,
    "city": "Washington",
    "country": "USA"
  },
  "votes": 100
};

function validateObject(schema, p) {
	
}

Return Ex:
{valid : false, errors :[ “zip type is string but input is int” ]}
{ valid : true, errors ; []}

Use this online tool for compiling your code https://www.programiz.com/javascript/online-compiler/

//Answer not correct
const validateObjectSchema = (schema, p) => {
    let res = {
        valid : null,
        error : []
    }
    for (x in p){
        if(!schema[x]){
            let newError = `Field ${x} is not in schema`
            res.error.push(newError)
            res.valid = false
            
          
        }else{
            if(typeof(x) !== typeof(schema[x])){
                let newError = `${x} type is ${typeof(schema[x])} but input is ${typeof(x)}`
                res.error.push(newError)
                res.valid = false
                
                
            }else{
                res.valid = true
            }
            
        }
    }
    
    return res
}

console.log(validateObjectSchema(schema, p))
