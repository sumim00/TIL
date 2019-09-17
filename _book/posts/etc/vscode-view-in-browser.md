## vscode에서 html 파일 크롬 브라우저로 확인하기	

1. `ctrl` + `shift` + `p` (혹은 `F1`) 을 눌러 커맨드 창을 켠다. 
2. `Tasks: Configure Task` 를 클릭하고 `task.json` 파일 만들기로 넘어간다. 

3. ```task.json``` 파일 안에 있는 기존 내용을 모두 지우고 다음 코드를 추가한다.

   **command 부분은 사용자 각자의 크롬 경로에 맞춰 설정한다. 

```
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Chrome",
            "type": "process",
            "command": "chrome.exe",
            "windows": {
                "command": "C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe"
            },
            "args": [
                "${file}"
            ],
            "problemMatcher": []
        }
    ]
}
```

4. 저장하고 넘어온 뒤 html파일로 돌아와 `ctrl` + `shift` + `b` 를 누르면, 크롬 브라우저에서 해당 html 화면이 나타남을 확인할 수 있다.



### reference

https://stackoverflow.com/questions/30039512/how-to-view-my-html-code-in-browser-with-visual-studio-code