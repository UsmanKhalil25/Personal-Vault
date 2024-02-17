- Using get
```C++
#include<iostream>  
#include<fstream>  
  
using namespace std;  
  
int main(){  
    ifstream obj("file.txt",ios::in);  
    char ch;  
    while(obj){  
        obj.get(ch);  
        cout<<ch;  
    }  
    return 0;  
}
```

- eof()
```C++
#include<iostream>  
#include<fstream>  
  
using namespace std;  
  
int main(){  
    ifstream obj("file.txt",ios::in);  
    char ch;  
    while(!obj.eof()){  
        obj.get(ch);  
        cout<<ch;  
    }  
    return 0;  
}
```
- Another way to use get
```C++
#include<iostream>  
#include<fstream>  
  
using namespace std;  
  
int main(){  
    ifstream obj("file.txt",ios::in);  
    char ch;  
    while(!obj.eof()){  
        ch  = obj.get();  
        cout<<ch;  
    }  
    return 0;  
}
```

- Using obj and >> operator
```C++
#include<iostream>  
#include<fstream>  
  
using namespace std;  
  
int main(){  
    ifstream obj("file.txt",ios::in);  
    string word;  
    while(!obj.eof()){  
        obj>>word;  
        cout<<word;  
    }  
    obj.close();  
    return 0;  
}
```

```C++
#include<iostream>  
#include<fstream>  
  
using namespace std;  
  
int main(){  
    ifstream obj("file.txt",ios::in);  
    char sentence[100];  
    while(!obj.eof()){  
        obj.getline(sentence,50,'\0');  
        cout<<sentence;  
  
    }  
    obj.close();  
    return 0;  
}
```
