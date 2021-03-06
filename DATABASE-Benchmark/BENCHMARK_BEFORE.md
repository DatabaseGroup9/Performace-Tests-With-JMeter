## Benchmarking before optimization

1. Given a city name your application returns all book titles with corresponding authors that mention this city.
2. Given a book title, your application plots all cities mentioned in this book onto a map.
3. Given an author name, your application lists all books written by that author and plots all cities mentioned in any of the books onto a map.
4. Given a geolocation, your application lists all books mentioning a city in vicinity of the given geolocation. 


Running the following commands returns empty lit because the respective databases has not been indexed or optimized.

MongoDB

```db.getCollection('books2').getIndexes()```


Neo4J

```CALL db.indexes```


[![https://gyazo.com/650479376637b1498330604ef6d26a71](https://i.gyazo.com/650479376637b1498330604ef6d26a71.png)](https://gyazo.com/650479376637b1498330604ef6d26a71)

### Performance Story 1

[![https://gyazo.com/9f76f59c458f33df7eef21832b928dd2](https://i.gyazo.com/9f76f59c458f33df7eef21832b928dd2.png)](https://gyazo.com/9f76f59c458f33df7eef21832b928dd2)

### Performance Story 2

[![https://gyazo.com/11b733f80d666ba6c21b5a0a1bcad3ac](https://i.gyazo.com/11b733f80d666ba6c21b5a0a1bcad3ac.png)](https://gyazo.com/11b733f80d666ba6c21b5a0a1bcad3ac)

### Performance Story 3

[![https://gyazo.com/adf13a02318adfe40000fd4da66fbb43](https://i.gyazo.com/adf13a02318adfe40000fd4da66fbb43.png)](https://gyazo.com/adf13a02318adfe40000fd4da66fbb43)

### Performance Story 4

[![https://gyazo.com/258c81118c72fea7460ea25bbfee005e](https://i.gyazo.com/258c81118c72fea7460ea25bbfee005e.png)](https://gyazo.com/258c81118c72fea7460ea25bbfee005e)