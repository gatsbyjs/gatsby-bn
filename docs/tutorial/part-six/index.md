---
title: ট্রান্সফর্মার প্লাগইনসমূহ
typora-copy-images-to: ./
disableTableOfContents: true
---

> এই টিউটোরিয়ালটি Gatsby এর ডেটা লেয়ার সম্পর্কিত সিরিজের অংশ। [পার্ট ৪](/tutorial/part-four/) এবং [পার্ট ৫](/tutorial/part-five/) সম্পন্ন করেছেন কিনা নিশ্চিত হয়ে এটি শুরু করুন।

## কি আছে এই টিউটোরিয়ালে?

এর আগের টিউটোরিয়ালে দেখানো হয়েছে কিভাবে সোর্স প্লাগইনগুলি ডেটা Gatsby এর ডেটা সিস্টেমে _নিয়ে আসে_। এই টিউটোরিয়ালে আপনি শিখবেন, সোর্স প্লাগইন গুলির নিয়ে আসা Raw ডেটা কিভাবে ট্রান্সফর্মার প্লাগইনগুলি _পরিবর্তন_ করে। Gatsby সাইট তৈরির সময় সোর্স প্লাগইন এবং ট্রান্সফর্মার প্লাগইন এর সমন্বয় করে প্রয়োজনীয় সকল ডেটা সোর্সিং এবং ডেটা পরিবর্তন নিয়ন্ত্রণ করতে পারবেন।

## ট্রান্সফর্মার প্লাগইনসমূহ

প্রায়শই, আপনার সাইট তৈরির সময় সোর্স প্লাগইনের মাধ্যমে প্রাপ্ত ডেটার ফরমেট দরকার
মতো হয় না। ফাইলসিস্টেম সোর্স প্লাগইন আপনাকে ফাইলের _সম্পর্কে_ ডেটা Query করতে
দেয় কিন্তু আপনি যদি ফাইলের _অভ্যন্তরীণ_ ডেটা Query করতে চান, সেটা সম্ভব হয় কি?

এটা সম্ভব করতে, Gatsby ট্রান্সফর্মার প্লাগইন সাপোর্ট করে, যা সোর্স প্লাগইনগুলির Raw কন্টেট
গ্রহণ করে সেটা _পরিবর্তন_ করে অধিক ব্যবহারযোগ্য করে তুলে।

উদাহরণস্বরূপ, মার্কডাউন ফাইলকেই ধরি। মার্কডাউন ফরমেটে লিখতে অনেক সুবিধা হয়,
কিন্ত সাইট তৈরির সময় মার্কডাউন ফাইল এইচটিএমএল (HTML) ফরমেটে থাকতে হয়।

আপনার সাইটে `src/pages/sweet-pandas-eating-sweets.md` 
এরকম একটা মার্কডাউন যোগ করুন (এটা আপনার প্রথম মার্কডাউন ব্লগপোস্ট হবে) এবং 
কিভাবে এটাকে ট্রান্সফর্মার প্লাগইন আর GraphQL ব্যবহার করে HTML ফরমেটে _পরিবর্তন_ করবেন
তা শিখুন।

```markdown:title=src/pages/sweet-pandas-eating-sweets.md
---
title: "Sweet Pandas Eating Sweets"
date: "2017-08-10"
---

Pandas are really sweet.

Here's a video of a panda eating sweets.

<iframe width="560" height="315" src="https://www.youtube.com/embed/4n0xNbfJLR8" frameborder="0" allowfullscreen></iframe>
```

এবার ফাইলটি সেইভ করবার পরে,  `/my-files/` এ আবার দেখুন- নতুন মার্কডাউন ফাইল টেবিলে
যুক্ত হয়েছে। এটা  Gatsby এর খুবই শক্তিশালী একটি ফিচার। আগের উদাহরণের `siteMetadata`
মতো, সোর্স প্লাগইন ডেটা লাইভ-রিলোড করতে পারে।
`gatsby-source-filesystem` সর্বদা নতুন ফাইল যুক্ত করার জন্য খোজ করতে থাকে এবং
পেয়ে গেলে আপনার query গুলো পুনরায় চালায়।

মার্কডাউন ফাইলগুলি পরিবর্তন করতে পারে এমন একটা ট্রান্সফর্মার প্লাগইন যুক্ত করুন:

```shell
npm install --save gatsby-transformer-remark
```

এরপর এটাকে নরমালের মতো `gatsby-config.js` এ যুক্ত করুন:

```javascript:title=gatsby-config.js
module.exports = {
  siteMetadata: {
    title: `Pandas Eating Lots`,
  },
  plugins: [
    {
      resolve: `gatsby-source-filesystem`,
      options: {
        name: `src`,
        path: `${__dirname}/src/`,
      },
    },
    `gatsby-transformer-remark`, // highlight-line
    `gatsby-plugin-emotion`,
    {
      resolve: `gatsby-plugin-typography`,
      options: {
        pathToConfigModule: `src/utils/typography`,
      },
    },
  ],
}
```

ডেভেলপমেন্ট সার্ভার রিস্টার্ট করে GraphiQL রিফ্রেস করুন (অথবা পূনরায় খুলুন) এবং 
Autocomplete টা দেখুন:

![markdown-autocomplete](markdown-autocomplete.png)

আবার `allMarkdownRemark` সিলেক্ট করুন এবং এটাকে `allFile` যেভাবে চালিয়েছিলেন
সেভাবে চালান। আপনি সেখানে নতুন যুক্ত করা মার্কডাউন ফাইল দেখতে পাবেন।
`MarkdownRemark` নোড এর ফিল্ডগুলি ঘুরে দেখুন।

![markdown-query](markdown-query.png)

আচ্ছা! আশা করি, কিছু বেসিক ধারণা পাচ্ছেন। Gatsby এর ডেটা সিস্টেমে
সোর্স প্লাগইনগুলি ডেটা _নিয়ে আসে_ এবং _ট্রান্সফর্মার_ প্লাগইনগুলি সোর্স প্লাগইনের
আনা Raw কন্টেন্ট  পরিবর্তন করে। এইভাবে আপনার সাইটের প্রয়োজনীয় সকল
সোর্সিং এবং ট্রান্সফর্মেশন পরিচালনা করতে পারবেন।

## আপনার সাইটের মার্কডাউন ফাইলসমুহের লিস্ট `src/pages/index.js` এ তৈরি করুন

এখন প্রথম পেইজে আপনার মার্কডাউন ফাইলগুলির লিস্ট তৈরি করতে হবে। অন্য অনেক ব্লগের
মত, আপনি হয়তো প্রথম পেইজে এমন লিংকের লিস্ট চাইবেন যা ব্লগপোস্ট গুলোকে পয়েন্ট করবে।
GraphQL এর মাধ্যমে বর্তমান মার্কডাউন ব্লগপোস্ট গুলির লিস্ট মেনুয়ালি মেইন্টেইন
না করে _Query_ করে পেতে পারেন।

`src/pages/my-files.js` এর যেভাবে করেছিলেন সেভাবে, `src/pages/index.js` কে নিচের
GraphQL query সাথে কিছু প্রাথমিক HTML এবং Styling কোড দিয়ে  রিপ্লেস করুন।

```jsx:title=src/pages/index.js
import React from "react"
import { graphql } from "gatsby"
import { css } from "@emotion/core"
import { rhythm } from "../utils/typography"
import Layout from "../components/layout"

export default ({ data }) => {
  console.log(data)
  return (
    <Layout>
      <div>
        <h1
          css={css`
            display: inline-block;
            border-bottom: 1px solid;
          `}
        >
          Amazing Pandas Eating Things
        </h1>
        <h4>{data.allMarkdownRemark.totalCount} Posts</h4>
        {data.allMarkdownRemark.edges.map(({ node }) => (
          <div key={node.id}>
            <h3
              css={css`
                margin-bottom: ${rhythm(1 / 4)};
              `}
            >
              {node.frontmatter.title}{" "}
              <span
                css={css`
                  color: #bbb;
                `}
              >
                — {node.frontmatter.date}
              </span>
            </h3>
            <p>{node.excerpt}</p>
          </div>
        ))}
      </div>
    </Layout>
  )
}

export const query = graphql`
  query {
    allMarkdownRemark {
      totalCount
      edges {
        node {
          id
          frontmatter {
            title
            date(formatString: "DD MMMM, YYYY")
          }
          excerpt
        }
      }
    }
  }
`
```

এখন প্রথম পেইজ দেখতে এমন হবে:

![frontpage](frontpage.png)

কিন্তু আপনার একটা ব্লগপোস্টকে একটু একা একা লাগছে। তাই চলুন আরো একটা ব্লগপোস্ট 
`src/pages/pandas-and-bananas.md` এ যোগ করি।

```markdown:title=src/pages/pandas-and-bananas.md
---
title: "Pandas and Bananas"
date: "2017-08-21"
---

Do Pandas eat bananas? Check out this short video that shows that yes! pandas do
seem to really enjoy bananas!

<iframe width="560" height="315" src="https://www.youtube.com/embed/4SZl1r2O_bY" frameborder="0" allowfullscreen></iframe>
```

![two-posts](two-posts.png)

এটা দারুন দেখাচ্ছে! শুধু... পোস্টের অর্ডার ঠিক নেই।

কিন্তু এটা খুব সহজে ঠিক করা যায়। যখন কোনো টাইপের কানেকশন query করবেন, আপনি
বিভিন্ন প্রকার আর্গুমেন্ট GraphQL query তে পাঠাতে পারেন। আপনি নোডগুলো `sort` এবং `filter`
করতে পারেন, কতগুলো নোড `skip` করবে নির্দিস্ট করে দিতে পারেন, এবং কয়টি নোড আনবেন সেই `limit`
নির্দিস্ট করে দিতে পারেন। এই শক্তিশালী অপারেটরের সেট ব্যবহার করে আপনি আপনার প্রয়োজনীয় যেকোন ডেটা,
যেকোনো ফরমেটে পেতে পারেন।

আপনার index পেইজে GraphQL query তে `allMarkdownRemark` কে
`allMarkdownRemark(sort: { fields: [frontmatter___date], order: DESC })` এ পরিবর্তন করুন। _নোট: এখানে `frontmatter` এবং`date` এর মধ্যে ৩ টা আন্ডারস্কোর  আছে।_ এটা
সেইভ করুন, এর মাধ্যমে সর্ট অর্ডার ঠিক হয়ে যাবে।

GraphiQL ওপেন করে বিভিন্ন সর্ট অপশন চেস্টা করে দেখুন। আপনি `allFile` কানেশন
সহ সকল কানেকশন সর্ট করতে পারবেন।

Query অপারেটর সমূহের আরো ডকুমেন্টেশনের জন্য, আমাদের [GraphQL রেফারেন্স গাইড](/docs/graphql-reference/) ঘুরে দেখতে পারেন।

## চ্যালেঞ্জ

একটা নতুন ব্লগপোস্ট পেইজ তৈরি করার চেস্টা করুন এবং হোম পেইজের ব্লগ পোস্টের লিস্টে কি পরিবর্তন হয় দেখুন!

## এরপর কি আসছে?

অনেক দারুণ লাগছে! আপনি মাত্রই একটা Index পেইজ তৈরি করেছেন যেখানে আপনি মার্কডাউন ফাইল্গুলো
Query করছেন এবং একটি ব্লগপোস্টের টাইটেল এবং উদ্ধৃতাংশ (Excerpt) এর লিস্ট তৈরি করছেন। কিন্তু আপনি শুধু উদ্ধৃতাংশ চান না, আপনি মার্কডাউন ফাইলের আসল পেইজ চান।

আপনি `src/pages` এ React কম্পোনেন্ট বসানো শেখা চালিয়ে যেতে পারেন। যাহোক, আপনি
এরপর শিখবেন কিভাবে _প্রোগ্রামেটিকালি_ ডেটা থেকে পেইজ তৈরি করতে পারবেন। অন্যান্য স্টেটিক সাইট জেনারেটরের মতো,
Gatsby শুধু ফাইল থেকে পেইজ তৈরিতে সীমাবদ্ধ _না_।  Gatsby আপনাকে GraphQL ব্যাবহার করে _ডেটা_ এবং _ম্যাপ_
Query করতে দেয় এবং _রেজাল্ট_ এ Query করতে দেয় - সবই বিল্ডটাইমে।
এটা অনেক শক্তিশালী কৌশল। পরের টিউটোরিয়ালে আপনি এর প্রভাব এবং
এটা কিভাবে ব্যবহার করবেন তা দেখতে পাবেন, যেখানে আপনি শিখবেন কিভাবে [প্রোগ্রামিটিকালি ডেটা থেকে পেইজ তৈরি করে](/tutorial/part-seven/)।
