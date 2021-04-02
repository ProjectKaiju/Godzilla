Use Cases
=========

## Overall Use Cases
```puml
@startuml
left to right direction
actor :Web User: << Human / Bot >> as WebUser

rectangle Browser{
    rectangle HTTP {
        usecase (GET Resource) as HttpGet
        usecase (POST Resource) as HttpPost
        usecase (PUT Resource) as HttpPut
        usecase (DELETE Resource) as HttpDelete
    }

    rectangle HTML {
        usecase (Manipulates DOM) as ManipDom
    }
}

WebUser =d=> ManipDom : Invoke

WebUser =r=> HttpGet : Invoke
WebUser =r=> HttpPost : Invoke
WebUser =r=> HttpPut : Invoke
WebUser =r=> HttpDelete : Invoke
@enduml

```

### UC List

* [GET Resource (HttpGet)](Http.md#httpget)
* [POST Resource (HttpPost)](Http.md#httppost)
* [PUT Resource (HttpPut)](Http.md#httpput)
* [DELETE Resource (HttpDelete)](Http.md#httpdelete)

## Godzilla Use Cases

![uncached image](http://www.plantuml.com/plantuml/proxy?cache=no&src=https://raw.githubusercontent.com/ProjectKaiju/Godzilla/main/docs/use_cases/Godzilla%20Use%20Cases.puml)



```puml
@startuml
left to right direction

skinparam actorStyle awesome

actor Godzilla << Server >>
note bottom of Godzilla
    Godzilla is Hosted in IIS or
    another web server.
end note

rectangle Browser{
    rectangle HTTP {
        usecase (GET Resource) as HttpGet
        usecase (POST Resource) as HttpPost
        usecase (PUT Resource) as HttpPut
        usecase (DELETE Resource) as HttpDelete
    }

    rectangle WebSocket {
        usecase (Read Resource) as ReadRes
        usecase (Save Resource) as SaveRes
        usecase (Remove Resource) as RemoveRes
        usecase (Send Notification) << Event >> as Notification
    }
}

Godzilla <=l= ReadRes
Godzilla <=l= SaveRes
Godzilla <=l= RemoveRes

Godzilla =d=> Notification

Godzilla <=u= HttpGet
Godzilla <=u= HttpPost
Godzilla <=u= HttpPut
Godzilla <=u= HttpDelete
@enduml
```

### UC List

* [Read Resource (ReadRes)](WebSocket.md#readres)
* [Save Resource (SaveRes)](WebSocket.md#saveres)
* [Remove Resource (RemoveRes)](WebSocket.md#removeres)
* [Send Notification (Notification)](WebSocket.md#notification)
