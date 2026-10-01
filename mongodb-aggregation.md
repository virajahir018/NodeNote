# MongoDB Aggregation Notes

## 1. Aggregation kya hai?

MongoDB mein **Aggregation** ek data processing pipeline hai.

Iska use data par different operations perform karne ke liye hota hai, jaise:

* Filtering
* Grouping
* Sorting
* Calculation
* Joining
* Pagination
* Data formatting

Simple words mein:

> **Aggregation ek pipeline hai jisme data ek stage se doosri stage mein process hota hua final result tak pahuchta hai.**

---

# 2. Aggregation Pipeline

Aggregation ke andar ek **pipeline** hoti hai.

Pipeline ke andar multiple **stages** hote hain.

Har stage ka output next stage ka input ban jata hai.

```text
Raw Data
   ↓
$match
   ↓
$group
   ↓
$sort
   ↓
$project
   ↓
Final Result
```

Isko aap **Factory Assembly Line** ki tarah samajh sakte ho:

```text
Raw Material
     ↓
  Stage 1
     ↓
  Stage 2
     ↓
  Stage 3
     ↓
Final Product
```

---

# 3. Important Aggregation Stages

MongoDB Aggregation ke commonly used stages:

| Stage        | Purpose                                             |
| ------------ | --------------------------------------------------- |
| `$match`     | Data filter karta hai                               |
| `$group`     | Data ko group karke calculation karta hai           |
| `$sort`      | Data ko order mein arrange karta hai                |
| `$project`   | Fields ko select/hide/modify karta hai              |
| `$lookup`    | Dusre collection ke saath data join karta hai       |
| `$unwind`    | Array ko individual documents mein expand karta hai |
| `$addFields` | New fields add karta hai                            |
| `$skip`      | Starting ke documents skip karta hai                |
| `$limit`     | Maximum documents ki limit set karta hai            |
| `$facet`     | Multiple pipelines ko ek saath run karta hai        |

---

# 4. `$match`

`$match` ka use data ko **filter** karne ke liye hota hai.

Ye conceptually `.find()` ke filtering part jaisa hai.

Example:

```javascript
{
  $match: {
    status: "completed"
  }
}
```

Iska matlab:

> Sirf wahi documents aage jayenge jinka `status` `"completed"` hai.

---

# 5. `$group`

`$group` ka use similar data ko group karke calculations karne ke liye hota hai.

Isse hum:

* Sum
* Average
* Count
* Maximum
* Minimum

jaise calculations kar sakte hain.

Example:

```javascript
{
  $group: {
    _id: "$customerId",
    totalSpent: {
      $sum: "$price"
    }
  }
}
```

Yahan:

```text
_id → customerId ke basis par grouping
$sum → price ka total
totalSpent → calculated field
```

---

# 6. `$sort`

`$sort` data ko ascending ya descending order mein arrange karta hai.

Example:

```javascript
{
  $sort: {
    totalSpent: -1
  }
}
```

### Values

```text
1   → Ascending
-1  → Descending
```

Example:

```text
100
500
1000
```

Descending:

```text
1000
500
100
```

---

# 7. `$project`

`$project` ka use output mein fields ko:

* Show karne
* Hide karne
* Rename/format karne
* New calculated fields banane

ke liye kiya ja sakta hai.

### Basic Example

```javascript
{
  $project: {
    password: 0,
    name: 1,
    email: 1
  }
}
```

Yahan:

```text
1 → Field include
0 → Field exclude
```

---

## `$project` se New Field Banana

Hum existing fields ko combine karke new field bhi bana sakte hain.

Example:

```javascript
{
  $project: {
    name: 1,
    email: 1,

    fullName: {
      $concat: [
        "$firstName",
        " ",
        "$lastName"
      ]
    }
  }
}
```

Agar:

```text
firstName = Rahul
lastName  = Sharma
```

to:

```text
fullName = Rahul Sharma
```

---

# 8. `$lookup`

`$lookup` ka use **do collections ke data ko join** karne ke liye hota hai.

SQL mein ise `JOIN` ke concept se compare kar sakte hain.

### Example

Maan lo hamare paas:

```text
orders
users
```

Orders collection mein:

```javascript
{
  userId: 101,
  price: 500
}
```

Users collection mein:

```javascript
{
  _id: 101,
  name: "Rahul"
}
```

Hume order ke saath user ki information bhi chahiye.

Iske liye `$lookup` use kar sakte hain.

---

## `$lookup` ke Important Fields

| Field          | Meaning                                  |
| -------------- | ---------------------------------------- |
| `from`         | Kis collection se data lana hai          |
| `localField`   | Current collection ki matching field     |
| `foreignField` | Other collection ki matching field       |
| `as`           | Result ko kis field mein store karna hai |

Example:

```javascript
{
  $lookup: {
    from: "users",
    localField: "userId",
    foreignField: "_id",
    as: "userInfo"
  }
}
```

### Important

`$lookup` ka result normally **array** ke form mein aata hai.

Example:

```javascript
{
  userInfo: [
    {
      name: "Rahul",
      email: "rahul@example.com"
    }
  ]
}
```

---

# 9. `$unwind`

`$unwind` ka use array ko expand karne ke liye hota hai.

Suppose:

```javascript
{
  name: "Rahul",
  hobbies: [
    "Cricket",
    "Music"
  ]
}
```

`$unwind` ke baad array ke elements separate documents ki form mein process ho sakte hain.

---

## `$lookup` + `$unwind`

`$lookup` ke baad data generally array mein aata hai.

Example:

```javascript
{
  customer: [
    {
      name: "Rahul",
      email: "rahul@example.com"
    }
  ]
}
```

Ab:

```javascript
{
  $unwind: "$customer"
}
```

ke baad:

```javascript
{
  customer: {
    name: "Rahul",
    email: "rahul@example.com"
  }
}
```

### Simple Trick

```text
$lookup  → Data ko join karta hai
$unwind  → Array ko expand karta hai
```

---

# 10. `$addFields`

`$addFields` ka use existing document mein **new field add** karne ke liye hota hai.

Example:

```javascript
{
  $addFields: {
    totalPriceWithTax: {
      $multiply: [
        "$price",
        1.18
      ]
    }
  }
}
```

Agar:

```text
price = 1000
```

to:

```text
totalPriceWithTax = 1180
```

---

# 11. `$skip`

`$skip` starting ke documents ko skip karta hai.

Example:

```javascript
{
  $skip: 10
}
```

Matlab:

> Starting ke 10 documents skip karo.

---

# 12. `$limit`

`$limit` maximum kitne documents result mein chahiye, ye define karta hai.

Example:

```javascript
{
  $limit: 10
}
```

Matlab:

> Maximum 10 documents return/process karo.

---

# 13. Pagination using `$skip` + `$limit`

Pagination mein `$skip` aur `$limit` ka commonly use hota hai.

Example:

```javascript
[
  {
    $skip: 10
  },
  {
    $limit: 10
  }
]
```

Iska simple meaning:

```text
First 10 documents → Skip
Next 10 documents  → Get
```

---

# 14. `$facet`

`$facet` ka use **multiple aggregation pipelines ko ek hi stage mein run** karne ke liye kiya jata hai.

Example:

Hume ek hi request mein:

1. Products ki list
2. Total products ka count

dono chahiye.

```javascript
{
  $facet: {
    productData: [
      { $skip: 0 },
      { $limit: 10 }
    ],

    totalCount: [
      { $count: "total" }
    ]
  }
}
```

Yahan do pipelines parallel structure mein define ki gayi hain:

```text
              $facet
             /      \
            /        \
 productData       totalCount
     ↓                 ↓
 products            count
```

---

# 15. `$cond`

`$cond` aggregation mein **if-else condition** ke liye use hota hai.

Example:

```javascript
{
  $project: {
    itemName: 1,

    status: {
      $cond: {
        if: {
          $gte: ["$stock", 10]
        },
        then: "Available",
        else: "Low Stock"
      }
    }
  }
}
```

Logic:

```text
अगर stock >= 10
       ↓
  "Available"

वरना
       ↓
  "Low Stock"
```

---

# 16. Aggregation Operators

Aggregation mein different operators calculations aur conditions ke liye use hote hain.

Examples:

```text
$sum
$multiply
$concat
$gte
$cond
$count
```

### `$sum`

Values ka total calculate karta hai.

```javascript
{
  $sum: "$price"
}
```

### `$multiply`

Values ko multiply karta hai.

```javascript
{
  $multiply: ["$price", 1.18]
}
```

### `$concat`

Strings ko combine karta hai.

```javascript
{
  $concat: [
    "$firstName",
    " ",
    "$lastName"
  ]
}
```

### `$gte`

Check karta hai:

```text
greater than or equal to
```

Example:

```javascript
{
  $gte: ["$stock", 10]
}
```

---

# 17. `.find()` vs `.aggregate()`

| `.find()`                                                                     | `.aggregate()`                                                 |
| ----------------------------------------------------------------------------- | -------------------------------------------------------------- |
| Mainly documents find/filter karne ke liye                                    | Complex data processing ke liye                                |
| Simple queries ke liye useful                                                 | Multiple stages combine kar sakte hain                         |
| Grouping/calculation limited                                                  | Grouping aur calculations kar sakte hain                       |
| Join ke liye normal `.find()` direct `$lookup` jaisa pipeline stage nahi deta | `$lookup` use kar sakte hain                                   |
| Simple data retrieval                                                         | Reports, dashboards aur complex transformations ke liye useful |

### Simple Rule

```text
Simple Data Retrieval
        ↓
      find()

Complex Data Processing
        ↓
    aggregate()
```

---

# 18. Basic Aggregation Example

Suppose `orders` collection mein data hai:

```javascript
{
  customerId: 101,
  price: 500,
  status: "completed"
}
```

Hume completed orders ke basis par customer ka total spending calculate karna hai.

```javascript
const mongoose = require('mongoose');
const Order = require('./models/Order');

async function getCustomerTotalSpending() {
  try {
    const result = await Order.aggregate([
      {
        $match: {
          status: "completed"
        }
      },

      {
        $group: {
          _id: "$customerId",
          totalSpent: {
            $sum: "$price"
          }
        }
      },

      {
        $sort: {
          totalSpent: -1
        }
      }
    ]);

    console.log(result);

  } catch (error) {
    console.error(
      "Error during aggregation:",
      error
    );
  }
}

getCustomerTotalSpending();
```

---

## Is Pipeline mein kya hua?

### Step 1 — `$match`

```javascript
{
  $match: {
    status: "completed"
  }
}
```

Sirf completed orders select hue.

---

### Step 2 — `$group`

```javascript
{
  $group: {
    _id: "$customerId",
    totalSpent: {
      $sum: "$price"
    }
  }
}
```

Customer ke according orders group hue aur total price calculate hua.

---

### Step 3 — `$sort`

```javascript
{
  $sort: {
    totalSpent: -1
  }
}
```

Sabse zyada spending wala customer pehle aayega.

---

# 19. Real-World E-commerce Aggregation

Ab ek complete example dekhte hain jisme multiple aggregation stages ek saath use ho rahe hain.

Maan lo hamare paas:

```text
orders
users
```

collections hain.

Hume:

* Delivered orders chahiye
* Price ₹500 ya usse zyada ho
* User information chahiye
* Tax calculate karna hai
* Customer name banana hai
* Price ke according sorting karni hai
* Pagination ke liye skip/limit use karna hai

---

## Complete Code

```javascript
const mongoose = require('mongoose');
const Order = require('./models/Order');

async function getAdvancedOrderReport() {
  try {
    const report = await Order.aggregate([

      // 1. $match
      {
        $match: {
          status: "delivered",
          price: {
            $gte: 500
          }
        }
      },

      // 2. $lookup
      {
        $lookup: {
          from: "users",
          localField: "userId",
          foreignField: "_id",
          as: "userInfo"
        }
      },

      // 3. $unwind
      {
        $unwind: "$userInfo"
      },

      // 4. $addFields
      {
        $addFields: {
          totalPriceWithTax: {
            $multiply: [
              "$price",
              1.18
            ]
          }
        }
      },

      // 5. $project
      {
        $project: {
          orderId: "$_id",
          price: 1,
          totalPriceWithTax: 1,
          status: 1,

          customerName: {
            $concat: [
              "$userInfo.firstName",
              " ",
              "$userInfo.lastName"
            ]
          },

          customerEmail: "$userInfo.email"
        }
      },

      // 6. $sort
      {
        $sort: {
          totalPriceWithTax: -1
        }
      },

      // 7. $skip
      {
        $skip: 0
      },

      // 8. $limit
      {
        $limit: 5
      }

    ]);

    console.log(
      "---- Final Aggregation Report ----"
    );

    console.log(
      JSON.stringify(report, null, 2)
    );

  } catch (error) {
    console.error(
      "Error creating report:",
      error
    );
  }
}

getAdvancedOrderReport();
```

---

# 20. Complete Pipeline Flow

Upar wale example ka flow:

```text
Orders
  │
  ▼
$match
  │
  │ delivered + price >= 500
  ▼
$lookup
  │
  │ User data join
  ▼
$unwind
  │
  │ userInfo array expand
  ▼
$addFields
  │
  │ Calculate tax
  ▼
$project
  │
  │ Select & format fields
  ▼
$sort
  │
  │ Highest price first
  ▼
$skip
  │
  │ Skip documents
  ▼
$limit
  │
  │ Maximum 5
  ▼
Final Result
```

---

# 21. Expected Output

Example output:

```json
[
  {
    "orderId": "651a2b3c4d5e6f7a8b9c0d11",
    "price": 1200,
    "totalPriceWithTax": 1416,
    "status": "delivered",
    "customerName": "Rahul Sharma",
    "customerEmail": "rahul@example.com"
  },
  {
    "orderId": "651a2b3c4d5e6f7a8b9c0d12",
    "price": 850,
    "totalPriceWithTax": 1003,
    "status": "delivered",
    "customerName": "Priya Patel",
    "customerEmail": "priya@example.com"
  }
]
```

---

# 22. Quick Revision

## `$match`

```text
Data Filter
```

Example:

```javascript
{
  $match: {
    status: "delivered"
  }
}
```

---

## `$group`

```text
Data Group + Calculation
```

Example:

```javascript
{
  $group: {
    _id: "$customerId",
    total: {
      $sum: "$price"
    }
  }
}
```

---

## `$sort`

```text
Data Order
```

```javascript
{
  $sort: {
    price: -1
  }
}
```

---

## `$project`

```text
Fields Select / Hide / Transform
```

---

## `$lookup`

```text
Collection Join
```

---

## `$unwind`

```text
Array Expand
```

---

## `$addFields`

```text
New Field Add
```

---

## `$skip`

```text
Documents Skip
```

---

## `$limit`

```text
Maximum Documents
```

---

## `$facet`

```text
Multiple Pipelines
```

---

## `$cond`

```text
If / Else Condition
```

---

# 23. Aggregation Cheat Sheet

| Stage        | Easy Meaning            | Common Use       |
| ------------ | ----------------------- | ---------------- |
| `$match`     | Filter                  | `WHERE`          |
| `$group`     | Group + Calculate       | `GROUP BY`       |
| `$sort`      | Order                   | `ORDER BY`       |
| `$project`   | Select/Transform fields | Data formatting  |
| `$lookup`    | Join collections        | `JOIN`           |
| `$unwind`    | Expand array            | Array processing |
| `$addFields` | Add field               | Calculations     |
| `$skip`      | Skip documents          | Pagination       |
| `$limit`     | Limit documents         | Pagination       |
| `$facet`     | Multiple pipelines      | List + Count     |
| `$cond`      | If/Else                 | Conditional data |

---

# 24. Interview Revision

### What is MongoDB Aggregation?

> MongoDB Aggregation is a data processing pipeline that allows us to filter, group, sort, calculate, join and transform documents using multiple stages.

### What is `$match`?

> `$match` is used to filter documents based on specified conditions.

### What is `$group`?

> `$group` groups documents based on a specified field and can perform calculations such as sum, average and count.

### What is `$lookup`?

> `$lookup` is used to join data from another collection.

### What is `$unwind`?

> `$unwind` deconstructs an array field and creates separate pipeline output for each array element.

### What is `$project`?

> `$project` is used to select, exclude or transform fields in the aggregation result.

### What is `$facet`?

> `$facet` allows multiple aggregation pipelines to run within a single aggregation stage.

### What is `$cond`?

> `$cond` is used to implement conditional logic similar to if-else.

---

# Final Aggregation Flow

```text
                 MongoDB Aggregation
                         │
                         ▼
                  Aggregation Pipeline
                         │
        ┌────────────────┼────────────────┐
        ▼                ▼                ▼
     $match           $group           $lookup
        │                │                │
        ▼                ▼                ▼
     Filter          Calculate           Join
                         │                │
                         │                ▼
                         │             $unwind
                         │                │
                         └───────┬────────┘
                                 ▼
                              $project
                                 │
                                 ▼
                             $addFields
                                 │
                                 ▼
                               $sort
                                 │
                                 ▼
                         $skip + $limit
                                 │
                                 ▼
                           Final Result
```
