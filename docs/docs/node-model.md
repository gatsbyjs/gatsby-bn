---
title: নোড মডেল
description: এই ডকুমেন্টেশনটি Gatsby-র GraphQL ডেটা লেয়ারের নোড মডেলগুলিকে ব্যাখ্যা করে
jsdoc: ["gatsby/src/schema/node-model.js"]
apiCalls: NodeModel
contentsHeading: Methods
---

`context.nodeModel` এর মাধ্যমে Gatsby তার অভ্যন্তরীণ ডেটা স্টোর এবং ক্যোয়ারী ক্ষমতাকে GraphQL ফিল্ড রিসোলভারগুলোতে প্রকাশ করে।

## ব্যবহারবিধি

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
