sequenceDiagram
    participant browser
    participant server

    Note right of browser: User types the note and clicks Save
    
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/notes

    Note right of server: Server saves the note

    server->>browser: 302 redirect to /notes

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "This is a new note by Jayesh", "date": "2026-07-05T13:25:25.404Z" }, ... ]
    deactivate server

    Note right of browser: Browser renders all the notes
