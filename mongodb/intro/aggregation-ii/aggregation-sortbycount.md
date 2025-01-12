---
author: Stefan-Stojanovic
type: normal
category: tip
---

# Aggregating with sortByCount


---

## Content

In the previous insight, we learned how to aggregate using the `$group` aggregation pipeline stage. Now we are going to discuss the `$sortByCount` aggregation stage.

The `$sortByCount` aggregation stage is used to group documents by a specified expression, count how many documents each group has and sort the documents by count in descending order.

Syntax:

```javascript
{ $sortByCount: <expression> }
```

Let's say we have a `pokemon` collection with `500` pokémon. Each pokémon has an `_id`, `name`, `type` and `power` field. However, there are some pokémon that also have a `secondType` field. We want to count and sort all pokémon by their `secondType` field. To achieve this you would write:

```javascript
db.pokemon.aggregate({
  $sortByCount: "$secondType"
})
```

Output:

```javascript
{ "_id": null, "count": 344 }
{ "_id": "Flying", "count": 41 }
{ "_id": "Poison", "count": 36 }
{ "_id": "Water", "count": 32 }
{ "_id": "Steel", "count": 29 }
{ "_id": "Ground", "count": 18 }
```

As you can see in the output of the example above, there is a `null` field with a count of `344`. Those are the documents(pokémon) without a `secondType` field and they are counted as well.


---

## Practice

What is the `$sortByCount` aggregation stage used for?

???

True or false?
The syntax for the `$sortByCount` stage is `{ $sortByCount:  <expression> }`.

???

- To group, count and sort files in descending order by a specified expression
- True
- To sort aggregation stages in ascending order and count the number of aggregation stages each document passed through
- False


---

## Revision

Let's say we have a collection named `students` with 2000 documents. Each student has a `name`, `studentId` and `averageGrade` field. Count all documents whose `averageGrade` is greater than `90` and sort them in descending order.

```javascript
db.students.???([
  {
    ???: { ???: { $gt: 90 } }
  },
  {
    ???: "$averageGrade"
  }
])
```

- `aggregate`
- `$match`
- `averageGrade`
- `$sortByCount`
- `$count`
- `$find`
- `STUDENTS`
- `name`
- `studentId`
