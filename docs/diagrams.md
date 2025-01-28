# Diagrams and figures using Mermaid

[mermaid]("https://mermaid.js.org/intro/")

You can find many useful example on this url. (This line was added through syncing with github)

## Class diagram

```mermaid
---
title: Animal example
---
classDiagram
    note "From Duck till Zebra"
    Animal <|-- Duck
    note for Duck "can fly\ncan swim\ncan dive\ncan help in debugging"
    Animal <|-- Fish
    Animal <|-- Zebra
    Animal : +int age
    Animal : +String gender
    Animal: +isMammal()
    Animal: +mate()
    class Duck{
        +String beakColor
        +swim()
        +quack()
    }
    class Fish{
        -int sizeInFeet
        -canEat()
    }
    

```



## Architecture design

```mermaid
architecture-beta
    service left_disk(disk)[Disk]
    service top_disk(disk)[Disk]
    service bottom_disk(disk)[Disk]
    service top_gateway(internet)[Gateway]
    service bottom_gateway(internet)[Gateway]
    junction junctionCenter
    junction junctionRight

    left_disk:R -- L:junctionCenter
    top_disk:B -- T:junctionCenter
    bottom_disk:T -- B:junctionCenter
    junctionCenter:R -- L:junctionRight
    top_gateway:B -- T:junctionRight
    bottom_gateway:T -- B:junctionRight


```



## GitGraph

```mermaid
    gitGraph
       commit
       commit
       branch develop
       commit
       commit
       commit
       checkout main
       commit
       commit
       merge develop
       commit
       commit



```



## Sequence diagram

```mermaid
sequenceDiagram
      actor me
      participant apiSrv as control plane<br><br>api-server
      participant etcd as control plane<br><br>etcd datastore
      participant cntrlMgr as control plane<br><br>controller<br>manager
      participant sched as control plane<br><br>scheduler
      participant kubelet as node<br><br>kubelet
      participant container as node<br><br>container<br>runtime
      me->>apiSrv: 1. kubectl create -f pod.yaml
      apiSrv-->>etcd: 2. save new state
      cntrlMgr->>apiSrv: 3. check for changes
      sched->>apiSrv: 4. watch for unassigned pods(s)
      apiSrv->>sched: 5. notify about pod w nodename=" "
      sched->>apiSrv: 6. assign pod to node
      apiSrv-->>etcd: 7. save new state
      kubelet->>apiSrv: 8. look for newly assigned pod(s)
      apiSrv->>kubelet: 9. bind pod to node
      kubelet->>container: 10. start container
      kubelet->>apiSrv: 11. update pod status
      apiSrv-->>etcd: 12. save new state
```





## Pie chart

```mermaid
pie title What Voldemort doesn't have?
         "FRIENDS" : 2
         "FAMILY" : 3
         "NOSE" : 45
```



## XY Chart

```mermaid
xychart-beta
    title "Sales Revenue"
    x-axis [jan, feb, mar, apr, may, jun, jul, aug, sep, oct, nov, dec]
    y-axis "Revenue (in $)" 4000 --> 11000
    bar [5000, 6000, 7500, 8200, 9500, 10500, 11000, 10200, 9200, 8500, 7000, 6000]
    line [5000, 6000, 7500, 8200, 9500, 10500, 11000, 10200, 9200, 8500, 7000, 6000]

```



## Kanban

```mermaid
---
config:
  kanban:
    ticketBaseUrl: 'https://mermaidchart.atlassian.net/browse/#TICKET#'
---
kanban
  Todo
    [Create Documentation]
    docs[Create Blog about the new diagram]
  [In progress]
    id6[Create renderer so that it works in all cases. We also add som extra text here for testing purposes. And some more just for the extra flare.]
  id9[Ready for deploy]
    id8[Design grammar]@{ assigned: 'knsv' }
  id10[Ready for test]
    id4[Create parsing tests]@{ ticket: MC-2038, assigned: 'K.Sveidqvist', priority: 'High' }
    id66[last item]@{ priority: 'Very Low', assigned: 'knsv' }
  id11[Done]
    id5[define getData]
    id2[Title of diagram is more than 100 chars when user duplicates diagram with 100 char]@{ ticket: MC-2036, priority: 'Very High'}
    id3[Update DB function]@{ ticket: MC-2037, assigned: knsv, priority: 'High' }

  id12[Can't reproduce]
    id3[Weird flickering in Firefox]

```