# 🎨 Comic Shack

Comic Shack is a web application designed to bring together fans of comics and manga into one easy-to-navigate platform. The goal of the project is to create a digital “comic shop” experience — a place where users can browse, discuss, and discover their favorite titles, from classic superhero stories to modern indie and manga series.

---

## 🧩 Project Overview

The project was inspired by the idea of combining the browsing experience of a comic store with the accessibility of a web app. Users will be able to:

- Browse comics and manga by genre or publisher
- Read summaries and issue details
- Save favorites or add them to a personal collection
- Post reviews or ratings for each series

This repository currently serves as the foundation for building and tracking the project. Development will focus first on front-end structure and API integration for comic data retrieval.

---

## 🧠 Objectives

- Learn version control using **Git** and **GitHub** for project tracking and collaboration
- Develop a structured, real-world web app with clean documentation
- Practice project organization and markdown formatting through a detailed README
- Use the repository as a portfolio example of software engineering practices

---

## 🗺️ User Flow Diagram

The following flowchart represents the **user journey** throughout the Comic Shack app — from browsing comics to viewing details and managing their collection.  
It shows how users interact with the app’s main pages and features.

```mermaid
flowchart LR
    A[Home / Browse] -->|Select title| B[Comic Detail]
    A -->|Search / Filter| A
    B -->|Add to Favorites| C[My Collection]
    C -->|Open title| B
    B -->|Back| A
```

## 🔁 Data Flow Diagram

This diagram illustrates how data moves through the system — from the public comic API to the user interface and local storage.
It emphasizes where user actions (searching, saving, and retrieving favorites) interact with backend data sources.

```mermaid
flowchart TB
    API[(Public Comic API)]
    APP[Comic Shack App]
    BROWSE[Browse Page]
    DETAIL[Comic Detail Page]
    COLL[My Collection]

    API -->|"GET /comics?genre=..."| APP
    APP --> BROWSE
    BROWSE -->|"Select title"| DETAIL
    DETAIL -->|"GET /comics/:id"| APP
    DETAIL -->|"Save to Collection"| COLL
    COLL -->|"List favorites"| DETAIL
```

## 🧱 Data Model

This entity-relationship diagram shows the planned database and data structure for Comic Shack.
It helps ensure each page has the correct data available — from user details to comic series, issues, and reviews.

```mermaid
classDiagram
    class User {
      +id: UUID
      +email: string
      +passwordHash: string
    }
    class Series {
      +id: string
      +title: string
      +publisher: string
      +genres: string[]
      +summary: string
      +coverUrl: string
    }
    class Issue {
      +id: string
      +seriesId: string
      +number: string
      +title: string
      +releaseDate: date
    }
    class Review {
      +id: string
      +seriesId: string
      +userId: UUID
      +rating: int
      +comment: string
      +createdAt: datetime
    }
    class Favorite {
      +userId: UUID
      +seriesId: string
      +addedAt: datetime
    }

    User "1" -- "many" Review : writes
    Series "1" -- "many" Issue : has
    Series "1" -- "many" Review : receives
    User "1" -- "many" Favorite : saves
    Series "1" -- "many" Favorite : is saved by
```

## 🖼️ Wireframes (UI)

> Note: Comic Shack is **not** a store—these screens cover browsing, details, and collection only.

### Browse Page

![Browse Page Wireframe](./images/home-example.png)

### Series Detail Page

![Series Detail Page Wireframe](./images/series-detail-example.png)
