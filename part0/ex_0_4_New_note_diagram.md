# Diagram for https://fullstackopen.com/en/part0/fundamentals_of_web_apps exercise 0.4: New note diagram

```mermaid
sequenceDiagram
    participant user
    participant browser
    participant server

    user->>browser: open browser
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code<br/>that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON data [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function<br/>that renders the notes

    user->>browser: writes new text in the box and clicks "save"

    Note right of browser: Browser collects the text<br/>from the input field

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note<br/>Form data: note=<text>

    activate server
    Note right of server: Server saves the note<br/>into the notes database/list
    server-->>browser: HTTP 302 Redirect<br/>Location: /exampleapp/notes
    deactivate server

    Note right of browser: Browser reloads the notes page

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document with updated notes list
    deactivate server

    Note right of browser: Browser renders the page<br/>including the newly created note

    browser->>user: see directly the page with the new notes
