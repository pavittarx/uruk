# Strings

```cpp

	include<string>
	
	string str = "Hello World!";
	cout<<str; // Hello World!
	
	cin>>str; // Reads till next whitespace
	getline(cin, str); // Read complete line

	str.length(); // size of the string
	str.pop_back(); // removes a character from back
	str.push_back("."); // adds to the back
	
	str[0]; // 0th character
	str.at(0); // 0th character
	
	str.substring(0, 5); // Hello
	size_t pos = str.find("World"); // searching
	str.replace(pos, 5, "Universe"); // replace World w/ Universe
	str.erase(pos, 7); // clears 7 characters from string
	
	// print string character basis
	for (char c : str) { 
		std::cout << c; // Prints each character in the string 
	}
	
	// print string w/ iterators
	for (auto it = str.begin(); it != str.end(); ++it) { 
		 std::cout << *it; // Prints each character 
	}
	
	// Print string in vector of strings
	for(const auto &s: str){
		cout<<s<<endl;
	}
	
	str+=' World'; // Hello World
	
	// Multiple strings
	str1 == str2 // compare strings
	str1.append(str2) // combine strings
	
	stoi("123"); // string to integer
	stof("0.125"); // string to float
	to_string(123); // integer to string

```


## String Streams

```cpp
	include <sstream>
	
	stringstream ss; 
	// stringstream ss("Hello"); is also fine.
	int num = 100;
	ss << num; // append data to stream
	
	ss.clear(); // clear stream state
	
	string st = "Hello World";
	ss<<x; // reads till first whitespace character, w/o affecting st.
	
	str = ss.str(); // Convert stream to string
	
	ss.str("Dawn of the Horizons."); // set a new stream
	string x; 
	ss>>x; // output stream to x
	
	// Load word by word into stream
	ss.clear();
	st = "Code Geass, Lelouch D Britannia";
	istringstream iss(st);
	
	string word;
	while(iss>>word){
		ss<<word<<" ";
	}
	
	ss.str(); // Code Geass, Lelouch D Britannia
	
```


# Containers


# Iterators



# Classes

```cpp
```

## Pointers
```cpp
```

