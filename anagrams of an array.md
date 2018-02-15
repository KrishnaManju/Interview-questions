# find the anagrams in an given array

To find the anagrams in an given array, first we need to sort the each item(string) in ana array, and then check if there are any anagrams. If find, save anagrams in an separate array and finally save all arrays in a resultant array.

``` javascript

function groupAnagram(array) {
  var dict = {},
      result = [];

  for (var i = 0; i < array.length; i++) {
    let sortedString = array[i].split('').sort().join('');
    
    if (dict[sortedString] === undefined) {
      dict[sortedString] = {};
    }
    
    dict[sortedString][array[i]] = true;
   }
   

  for (i in dict) {
    result.push(Object.keys(dict[i]));
  }

  return result;
}

var input = ["star", "rats", "star", "car", "arc", "arts","hello"];

console.log(groupAnagram(input));

```

Output : [["star", "rats", "arts"], ["car", "arc"], ["hello"]] 

### C#

``` C#
using System;
using System.Collections.Generic;


public class Program
{
	public static void Main()
	{
		string[] a = {"star","rats","tars","car","rac"};
		Program.Anagrams(a);
	}
	

	public static void Anagrams (string[] arr) {
		Dictionary<string,List<string>> d = new Dictionary<string,List<string>>();
		
		for(int i = 0; i < arr.Length; i++) {			
			List<string> temp = new List<string>();
			
			char[] arrPri = arr[i].ToCharArray();
			Array.Sort(arrPri);
			string word = new string(arrPri);
			
			if(d.ContainsKey(word)) {
				temp = d[word];
				temp.Add(arr[i]);
				d[word] = temp;
			}
			else {
				
				temp.Add(arr[i]);
				d[word] = temp;
			}
		}
		
		//display the output
		foreach(KeyValuePair<string, List<string>> kv in d ) {
		
			Console.Write("[ ");
			for(int i = 0; i < kv.Value.Count; i++) {
				
				if( i != kv.Value.Count -1 ) {
					Console.Write(kv.Value[i] + ", ");
				}
				else {
					Console.Write(kv.Value[i]);
				}
			}
			Console.Write("] ");

		}

	}		
	
}
```
