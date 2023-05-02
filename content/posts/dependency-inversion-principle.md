+++
title = "Dependency Inversion Principle"
date = "2023-05-02T10:37:34+06:00"
author = "fl4ssh"
authorTwitter = "" #do not include @
cover = ""
tags = ["", ""]
keywords = ["", ""]
description = ""
showFullContent = false
readingTime = false
hideComments = false
+++

# Small overview of Dependency Inversion Principle

Dependency Inversion Principle (or DIP) is one of SOLID principles and methodology to avoid highly coupled distribution and increase the re-usability of layer. 

It is different from Dependency Injection, which is used to provide dependency to an application class / layer. Whereas DIP is used to invert the responsibility of flow control in an application.

Formal definitions of DIP:
 - High-level modules should not depend on low-level modules. Both should depend on abstractions.
 - Abstractions should not depend on details. Instead, details should depend on abstractions.

Implementing DIP makes your code more flexible, maintainable, and easier to test. It is achieved by decoupling the components of your application by implementing DIP. 

Example of DIP:
```
type Repository interface {
    GetData(id int) ([]byte, error) 
}

type Service struct {
    repo Repository
}

func (s *Service) ProcessDataByID(id int) error {
    data, err := s.repo.GetData(id)
    if err != nil {
        return err
    }

    // process data
    return nil
}
```
In this example, we see that the service that processes data by ID is not limited by specific repository implementation, e.g. SQL database, or NoSQL database. All it knows is that it should obtain a data or an error from database. And it is sufficient to work without any issues.

So DIP is implemented by an abstraction in the face of interfaces in Golang. Let's consider the case that doesn't follow DIP principle:
```
type Repository struct {
    db *sql.Conn
}

func (r *Repository) GetData(id int) ([]data, error) {
    // do transaction or simple query to retrieve data
    rows, err := r.Query("SELECT * FROM table") 
    if err != nil {
        return nil, error
    }
    // process rows to obtain data, etc...
    return data, nil
}

type Service struct {
    repo *Repository
}

func (s *Service) ProcessDataByID(id int) error {
    data, err := s.repo.GetData(id)
    if err != nil {
        return err
    }

    // process data
    return nil
}
```
In this code example, we see that `Service` struct directly depends on `Repository`. To test this code, you will need specific implementation of `Repository` structure and initialize a connection to a database. This creates unnecessary complexities.
