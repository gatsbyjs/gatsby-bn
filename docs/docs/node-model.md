---
title: নোড মডেল
description: এই ডকুমেন্টেশনটি Gatsby-র GraphQL ডেটা লেয়ার নোডগুলির মডেল ব্যাখ্যা করে 
jsdoc: ["gatsby/src/schema/node-model.js"]
apiCalls: NodeModel
contentsHeading: Methods
---

Gatsby তার অভ্যন্তরীণ ডেটা স্টোর এবং ক্যোয়ারী ক্ষমতা GraphQL ফিল্ড রিসোলভারগুলিকে `context.nodeModel`-এ প্রকাশ করে।

## ব্যবহারের উদাহরণ

```javascript:title=gatsby-node.js
createResolvers({
  Query: {
    mood: {
      type: `String`,
      resolve(source, args, context, info) {
        const coffee = context.nodeModel.getAllNodes({ type: `Coffee` })
        if (!coffee.length) {
          return 😞
        }
        return 😊
      },
    },
  },
})
```
