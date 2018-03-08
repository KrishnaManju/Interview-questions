#Flatten Dictionary in C# language

Note: If a certain key is empty, it should be excluded from the output (see e in the example below).
```
input:  dict = {
            "Key1" : "1",
            "Key2" : {
                "a" : "2",
                "b" : "3",
                "c" : {
                    "d" : "3",
                    "e" : {
                        "" : "1"
                    }
                }
            }
        }

output: {
            "Key1" : "1",
            "Key2.a" : "2",
            "Key2.b" : "3",
            "Key2.c.d" : "3",
            "Key2.c.e" : "1"
        }
```
Solution: 
```C#
using System;
using System.Collections.Generic;

class Solution
{
  
  public static Dictionary<string, string> FlattenDictionary(Dictionary<string, object> dict)
  {
    Dictionary<string,string> res = new Dictionary<string,string>();
    Solution.FlattenDictionaryHelper("",dict,res);    
    return res;  
  }
  
  public static void FlattenDictionaryHelper(string startKey, Dictionary<string,object> dict, Dictionary<string,string> res) {
    
    foreach(var pair in dict) {      
        if(startKey == null || startKey == "") {
          if(pair.Value is string)
            res.Add(pair.Key, (string)pair.Value);
          else if(pair.Value is Dictionary<string,object>)
              FlattenDictionaryHelper( pair.Key, (Dictionary<string,object>)pair.Value, res);
        }
        else {
            if( pair.Value is Dictionary<string,object>){
               if(!String.IsNullOrEmpty(pair.Key)) 
                   FlattenDictionaryHelper(startKey +"." + pair.Key, (Dictionary<string,object>)pair.Value, res);
               else
                   FlattenDictionaryHelper(startKey, (Dictionary<string,object>)pair.Value, res);
             }
             else if(pair.Value is string) {   
                if(!String.IsNullOrEmpty(pair.Key)) 
                    res.Add(startKey +"." + pair.Key, (string)pair.Value);   
                else
                  res.Add(startKey, (string)pair.Value); 
             }    
         }
      }
    }

  public static void Main(string[] args)
  {    
  }
}
```
