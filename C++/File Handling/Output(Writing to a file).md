- ifstream to open a file in input mode (to read from a file)
- ofstream to open a file in output mode (to )
- Opening method
	- Using constructor 
	- Using open function
```C++
#include<iostream>  
#include<fstream>  
  
using namespace std;  
  
int main(){  
  
    fstream obj1("file1.txt",ios::out|ios::app);  
    //or  
    fstream obj2;  
    obj2.open("file2.txt",ios::out|ios::app);  
      
    return 0;  
}
```

- Writing to a file
```C++
#include<iostream>  
#include<fstream>  
  
using namespace std;  
  
int main(){  
  
    fstream obj("file.txt",ios::out|ios::app);  
    obj<<"Today is a good day"<<endl;  
    int number = 10;  
    obj<<"The value of number is: "<<number<<endl;  
  
  
  
    return 0;  
}
```

- Using member function put():
```C++
#include<iostream>  
#include<fstream>  
  
using namespace std;  
  
int main(){  
  
    fstream obj("file.txt",ios::out|ios::app);  
    obj<<"Today is a good day"<<endl;  
    int number = 10;  
    obj<<"The value of number is: "<<number<<endl;  
  
    string sentence = "This is a sentence";  
    for(int i = 0;sentence.length();i++)  
        obj.put(sentence[i]);  
    obj<<endl;  
    char arr[40] = "This is a character array";  
    obj.write(arr,40);  
  
    return 0;  
}
```

	