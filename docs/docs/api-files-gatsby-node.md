---
title: The gatsby-node.js API file
---

`gatsby-node.js` ফাইলের কোড একবার রান করা হয় আপনার সাইট তৈরি করার জন্য। আপনি এটি ব্যবহার করে dynamically পেইজ তৈরি করতে পারেন অথবা GraphQL এ node যুক্ত করতে পারেন অথবা build lifecycle events এ সাড়া দিতে পারেন। [Gatsby Node APIs](/docs/node-apis/) ব্যবহার করতে চাইলে `gatsby-node.js` নামে একটি ফাইল আপনার সাইটের মূল ফোল্ডারে তৈরি করুন। আপনি যেসব API ব্যবহার করতে চান এই ফাইলে, তা export করুন।

প্রতিটি Gatsby Node API [এক সেট সাহায্যকারী Node API](/docs/node-api-helpers/) সরবরাহ করে। এগুলো আপনাকে বিভিন্ন method ব্যবহার করতে দেয় যেমনঃ রিপোর্টিং অথবা নতুন কোনো পেইজ তৈরি করা।

```js:title=gatsby-node.js
const path = require(`path`)
// Log out information after a build is done
exports.onPostBuild = ({ reporter }) => {
  reporter.info(`Your Gatsby site has been built!`)
}
// Create blog pages dynamically
exports.createPages = async ({ graphql, actions }) => {
  const { createPage } = actions
  const blogPostTemplate = path.resolve(`src/templates/blog-post.js`)
  const result = await graphql(`
    query {
      allSamplePages {
        edges {
          node {
            slug
            title
          }
        }
      }
    }
  `)
  result.data.allSamplePages.edges.forEach(edge => {
    createPage({
      path: `${edge.node.slug}`,
      component: blogPostTemplate,
      context: {
        title: edge.node.title,
      },
    })
  })
}
```
