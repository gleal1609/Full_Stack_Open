## Quando o usuário adiciona uma nova nota na SPA

```mermaid
sequenceDiagram
    participant user
    participant browser
    participant server

    Note over user,browser: Usuário escreve no campo de texto e clica em submit

    Note right of browser: JavaScript usa preventDefault e evita o envio tradicional do formulário

    Note right of browser: "JS cria o objeto nota, adiciona à lista e redesenha a lista na página"

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note right of server: Servidor adiciona a nota ao array notes
    server-->>browser: 201 Created - sem redirecionamento
    deactivate server

    Note right of browser: Página permanece a mesma. Não há novo GET de HTML/CSS/JS nem data.json
```