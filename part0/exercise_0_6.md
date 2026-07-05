sequenceDiagram
    participant browser
    participant server

    Note right of browser: User types the note and clicks Save

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note right of server: Server saves the note
    server-->>browser: 201 {"message":"note created"}
    deactivate server

    Note right of browser: No page reload, no further GET requests