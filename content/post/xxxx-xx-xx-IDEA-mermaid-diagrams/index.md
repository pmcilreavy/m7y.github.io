+++
title = 'Mermaid Diagrams with Markdown'
summary = 'Mermaid Diagrams with Markdown.'
tags = ['docker', 'podman']
categories = ['development']
keywords = ['docker', 'podman']
date = 2024-05-01
draft = true
# [cover]
#     image = 'cover_image.webp'
#     alt = "Using an Azure function to get Octopus deployment notifications in Slack"
#     caption = "Image generated by Dall-E."
#     relative = true # when using page bundles set this to true
#     hidden = false # only hide on current single page
#     hiddenInSingle = false
+++

https://navendu.me/posts/adding-diagrams-to-your-hugo-blog-with-mermaid/

https://learn.microsoft.com/en-us/azure/devops/project/wiki/markdown-guidance?view=azure-devops
https://mermaid.js.org/syntax/flowchart.html
https://marketplace.visualstudio.com/items?itemName=bierner.markdown-mermaid
https://plugins.jetbrains.com/plugin/20146-mermaid
https://mermaid.live/
https://stackoverflow.com/questions/56885259/stop-vscode-preview-from-scrolling
https://c4model.com/

# Flowchart

https://mermaid.js.org/syntax/flowchart.html

```mermaid
flowchart TB
a1
a2
    subgraph one[One]
    a2 --x a1
    a1 --o a2

    end

    subgraph two[Sub System Two]
    b1-->b2
    end

    subgraph three[Sub System Three]
    c1-->c2
    end

    one --This is an arrow label--> two
    three --> two
```

# Flowchart (complex)

```mermaid
flowchart TB
classDef borderless stroke-width:0px
classDef darkBlue fill:#00008B, color:#fff
classDef brightBlue fill:#6082B6, color:#fff
classDef gray fill:#62524F, color:#fff
classDef gray2 fill:#4F625B, color:#fff

subgraph publicUser[ ]
    A1[[Public User<br/> Via REST API]]
    B1[Backend Services/<br/>frontend services]
end
class publicUser,A1 gray

subgraph authorizedUser[ ]
    A2[[Authorized User<br/> Via REST API]]
    B2[Backend Services/<br/>frontend services]
end
class authorizedUser,A2 darkBlue

subgraph booksSystem[ ]
    A3[[Books System]]
    B3[Allows interacting with book records]
end
class booksSystem,A3 brightBlue


publicUser--Reads records using-->booksSystem
authorizedUser--Reads and writes records using-->booksSystem

subgraph authorizationSystem[ ]
    A4[[Authorization System]]
    B4[Authorizes access to resources]
end

subgraph publisher1System[ ]
    A5[[Publisher 1 System]]
    B5[Gives details about books publshed by them]
end
subgraph publisher2System[ ]
    A6[[Publisher 2 System]]
    B6[Gives details about books publshed by them]
end
class authorizationSystem,A4,publisher1System,A5,publisher2System,A6 gray2

booksSystem--Accesses authorization details using-->authorizationSystem
booksSystem--Accesses publisher details using-->publisher1System
booksSystem--Accesses publisher details using-->publisher2System

class A1,A2,A3,A4,A5,A6,B1,B2,B3,B4,B5,B6 borderless

click A3 "/csymapp/mermaid-c4-model/blob/master/containerDiagram.md" "booksSystem"
```

# Sequence

https://mermaid.js.org/syntax/sequenceDiagram.html

```mermaid
sequenceDiagram
    Alice->>John: Hello John, how are you?
    John-->>Alice: Great!
    Alice-)John: See you later!
```

# Class

https://mermaid.js.org/syntax/classDiagram.html

```mermaid
classDiagram
class BankAccount{
    +String owner
    +BigDecimal balance
    +deposit(amount)
    +withdrawal(amount)
}
```

# State

https://mermaid.js.org/syntax/stateDiagram.html

```mermaid
stateDiagram-v2
    [*] --> Still
    Still --> [*]

    Still --> Moving
    Moving --> Still
    Moving --> Crash
    Crash --> [*]
```

# User Journey

https://mermaid.js.org/syntax/userJourney.html

```mermaid
journey
    title My working day
    section Go to work
      Make tea: 5: Me
      Go upstairs: 3: Me
      Do work: 1: Me, Cat
    section Go home
      Go downstairs: 5: Me
      Sit down: 5: Me
```

# Gantt

https://mermaid.js.org/syntax/gantt.html

```mermaid
gantt
    title A Gantt Diagram
    dateFormat YYYY-MM-DD
    section Section
        A task          :a1, 2014-01-01, 30d
        Another task    :after a1, 20d
    section Another
        Task in Another :2014-01-12, 12d
        another task    :24d
```

# Pie

https://mermaid.js.org/syntax/pie.html

```mermaid
pie title Pets adopted by volunteers
    "Dogs" : 386
    "Cats" : 85
    "Rats" : 15
```

# Requirement

https://mermaid.js.org/syntax/requirementDiagram.html

```mermaid
    requirementDiagram

    requirement test_req {
    id: 1
    text: the test text.
    risk: high
    verifymethod: test
    }

    element test_entity {
    type: simulation
    }

    test_entity - satisfies -> test_req
```

# Git Graph

https://mermaid.js.org/syntax/gitgraph.html

```mermaid

gitGraph:
    commit "Ashish"
    branch newbranch
    checkout newbranch
    commit id:"1111"
    commit tag:"test"
    checkout main
    commit type: HIGHLIGHT
    commit
    merge newbranch
    commit
    branch b2
    commit
```