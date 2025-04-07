<pre> ```mermaid
sequenceDiagram
    participant browser
        participant server

        Note right of browser: The user writes a note and clicks the Save button

        browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note with note data
        activate server
        server-->>browser: 302 Redirect to /exampleapp/notes
        deactivate server

        Note right of browser: The browser reloads the /exampleapp/notes page

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

        browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
        activate server
        server-->>browser: Updated JSON with the new note
        deactivate server

        Note right of browser: The browser executes the callback function that renders the updated notes
        ``` </pre>