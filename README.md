# GraphQL-Basics

GraphQL API with .NET 5 and Hot Chocolate Framework

I used <a href="https://www.nuget.org/packages/GraphQL.Server.Ui.Voyager/">this<a> extension for see the diagrams of table.

Use the this endpoint **/graphql-voyager** 

  
  
  
All request types are **POST** Method end endpoints are same **/graphql**
  
## GraphQL Queries

Get Platforms                                                                   
```
query{                                            
  platform{                                        
    id                                              
    name                                                
  }
}
```
Get Commands 
```
query{
  command{
    howTo
    commandLine
    platform{
      name
    }
  }
}
```
Get Platforms and Commands
```
query{
  platform{
    id
    name
    commands{
      id
      howTo
      commandLine
    }
  }
}
```
Parallel Platforms
```
query{
  a: platform{
    id
    name
  },
  b: platform{
    id
    name
  },
  c: platform{
    id
    name
  }
}
```
Filter Query
```
query {
    command(where: {platformId: {eq: 1}})
    {
        id
        platform{
            name
            id
        }
        commandLine
        howTo
    }
}
```
Sort Query
```
query {
  platform(order: {name: ASC}){
    name
  }
}
```

## GraphQL Mutations

Add Platform
```
mutation{
  addPlatform(input:{
    name: "Ubuntu"
  })
  {
    platform{
      id
      name
    }
  }
}
```
Add Command
```
mutation{
  addCommand(input: {
    howTo: "Perform directory listing"
    commandLine: "ls"
    platformId: 4
  })
  {
    command {
      id
      howTo
      commandLine
      platform{
        name
      }
    }
  }
}
```
