<div align="center">

## Console Keyboard Input


</div>

### Description

keyboard controlled text animation
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[T J Betsworth](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/t-j-betsworth.md)
**Level**          |Intermediate
**User Rating**    |5.0 (10 globes from 2 users)
**Compatibility**  |C\+\+ \(general\)
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__3-1.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/t-j-betsworth-console-keyboard-input__3-10905/archive/master.zip)





### Source Code

```
#include <windows.h>
#include <iostream>
#include <stdlib.h>
using namespace std;
     HANDLE hout= GetStdHandle(STD_OUTPUT_HANDLE);
     HANDLE hin = GetStdHandle(STD_INPUT_HANDLE);
     INPUT_RECORD InputRecord;
     DWORD Events;
     COORD coord;
     int x = 30;
     int y = 12;
 void erase(){
SetConsoleTextAttribute(hout,0);
cout<<"XXXXXXXXXXXXXX";
}
 void text(){
COORD coord = {x, y};
SetConsoleCursorPosition(hout, coord);
SetConsoleTextAttribute(hout,rand()%7+9);
cout<<"Planet Source!";
}
 void movetext(){
SetConsoleMode(hin, ENABLE_PROCESSED_INPUT);
ReadConsoleInput(hin, &InputRecord, 1, &Events);
    if(InputRecord.Event.KeyEvent.wVirtualKeyCode == VK_RIGHT)
    {
   erase();
   x++;
   text();
}
 else if(InputRecord.Event.KeyEvent.wVirtualKeyCode == VK_LEFT)
    {
   erase();
   x--;
   text();
}
 else if(InputRecord.Event.KeyEvent.wVirtualKeyCode == VK_UP)
    {
   erase();
   y--;
   text();
    }
 else if(InputRecord.Event.KeyEvent.wVirtualKeyCode == VK_DOWN)
    {
   erase();
   y++;
   text();
    }
FlushConsoleInputBuffer(hin);
}
int main()
{
cout<<"press any arrow key to start use arrow keys to move text\n"
   "keep text inside window Press Ctrl+C to Exit";
while(1)
{
  CONSOLE_CURSOR_INFO cci;
  cci.dwSize = 25;
  cci.bVisible = FALSE;
  SetConsoleCursorInfo(hout, &cci);
  COORD coord = {x, y};
  SetConsoleCursorPosition(hout, coord);
  movetext();
}
}
```

