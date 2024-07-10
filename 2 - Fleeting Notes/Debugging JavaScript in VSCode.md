
--- 
tags: [[Testing]] [[Visual Studio]] 
date: 2024-07-08

---
Run and debug
Web dev (Chrome)
nowy plik `.vscode` a w nim `launch.json` 
```js
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "type": "chrome",
            "request": "launch",
            "name": "Launch Chrome against localhost",
            "url": "http://localhost:8080",//sprawdź czy zgadzają się porty 5500
            "webRoot": "${workspaceFolder}"
        }
    ]
}
```


run and debug
launch chrome against local host
w body html wklej `<script src="nazwaPliku.js"></script>`

### References:

https://blogs.windows.com/msedgedev/2021/07/16/easier-debugging-developer-tools-in-visual-studio-code/


---



