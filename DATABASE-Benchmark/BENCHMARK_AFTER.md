## Benchmarking after optimization

1. Given a city name your application returns all book titles with corresponding authors that mention this city.
2. Given a book title, your application plots all cities mentioned in this book onto a map.
3. Given an author name, your application lists all books written by that author and plots all cities mentioned in any of the books onto a map.
4. Given a geolocation, your application lists all books mentioning a city in vicinity of the given geolocation. 


### MongoDB

[![https://gyazo.com/97f971c165da40b56bd3e39d7a95e064](https://i.gyazo.com/97f971c165da40b56bd3e39d7a95e064.png)](https://gyazo.com/97f971c165da40b56bd3e39d7a95e064)

### Neo4J

[![https://gyazo.com/3636532ce431a01fcac2d056f670ddaa](https://i.gyazo.com/3636532ce431a01fcac2d056f670ddaa.png)](https://gyazo.com/3636532ce431a01fcac2d056f670ddaa)

### MySQL

MySQL optimization consists of creating a SQL View:

```CREATE VIEW BooksTable AS
SELECT Books.bookID, Books.BookTitle, Cities.cityID, Cities.name, Cities.lat, Cities.lon, Author.authorID, Author.fullName, Author.firstName, Author.surName, Author.title FROM `Mentions` JOIN Books ON Mentions.bookID = Books.bookID JOIN Cities ON Mentions.cityID = Cities.cityID JOIN Wrote ON Wrote.bookID = Books.bookID JOIN Authors ON Authors.authorID = Wrote.authorID
```

### Performance Story 1
[![https://gyazo.com/cb765a7ae21407722c0d83e010c22ee2](https://i.gyazo.com/cb765a7ae21407722c0d83e010c22ee2.png)](https://gyazo.com/cb765a7ae21407722c0d83e010c22ee2)


### Performance Story 2
[![https://gyazo.com/4d8f0400f2413631af8e9f9accb40b43](https://i.gyazo.com/4d8f0400f2413631af8e9f9accb40b43.png)](https://gyazo.com/4d8f0400f2413631af8e9f9accb40b43)

### Performance Story 3

[![https://gyazo.com/e69781ec45c8e8492c62d7ebc131269b](https://i.gyazo.com/e69781ec45c8e8492c62d7ebc131269b.png)](https://gyazo.com/e69781ec45c8e8492c62d7ebc131269b)

### Performance Story 4

[![https://gyazo.com/e6a857503154c4fcc29d18c517d7efda](https://i.gyazo.com/e6a857503154c4fcc29d18c517d7efda.png)](https://gyazo.com/e6a857503154c4fcc29d18c517d7efda)

Quering The Databases

|   | Story 1 avg. ms |Story 2 avg. ms  | Story 3 avg. ms  | Story 4 avg. ms |
|---|---|---|---|---|
|  MongoDB | 689  | 42  |  49 | 234  |
|  Neo4J |  44  |  15 | 23  | 10  |
|  MySQL | 22  | 5  | 16  | 8  |



#### B. Query Runtime is influenced by the application frontend <br>

Quering The REST API

|   | Story 1 avg. ms |Story 2 avg. ms  | Story 3 avg. ms  | Story 4 avg. ms |
|---|---|---|---|---|
|  MongoDB | 5680  | 349  | 1072  | 3944  |
|  Neo4J |  1462 | 327  |  736 | 601  |
|  MySQL |  45 |  39 |  394 | 215  |
|  Stub |  61 |  36 |  42 | 41  |

Application Overhead 

*REST API time - query in the database*

|   | Story 1 avg. ms |Story 2 avg. ms  | Story 3 avg. ms  | Story 4 avg. ms |
|---|---|---|---|---|
|  MongoDB | 4991  | 307  | 1023  | 3710  |
|  Neo4J | 1323  |  222 | 572  | 562  |
|  MySQL | 23  | 34  | 378  | 207  |
