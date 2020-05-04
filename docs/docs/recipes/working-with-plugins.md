---
title: "রেসিপিঃ প্লাগিন নিয়ে কাজ করা"
tableOfContentsDepth: 1
---

একটি [Gatsby প্লাগিন](/docs/what-is-a-plugin/) Gatsby API-গুলোকে একটি ইন্সটল করা যায় এমন প্যাকেজে নিয়ে আসে। এর মানে আপনার প্রজেক্টে বিভিন্ন Gatsby ফাংশনালিটি সরাসরি সংযুক্ত হয়না, বরং কেন্দ্রীয়ভাবে নিয়ন্ত্রিত ভার্সনিং এর মাধ্যমে একটি ডিপেন্ডেন্সি হিসবে ইন্সটল হয়। আপনি এক্সটার্নাল ডাটা, ট্রান্সফর্ম ডাটা,থার্ড-পার্টি সার্ভিসসহ(যেমনঃ Google Analytics, Stripe) আরও অনেককিছুই আপনার প্রজেক্টে সংযুক্ত করতে পারেন।

## একটি প্লাগিন ব্যবহার করা

একটি প্লাগিন পেয়েছেন যা আপনার প্রজেক্টে ব্যবহার করতে চান? জোস! আপনি এটি ব্যবহার করার জন্য নিচের ধাপগুলি অনুসরণ করতে পারেন। এই রেসিপিতে উদাহরণস্বরূপ [`gatsby-source-filesystem` প্লাগিনটি](/packages/gatsby-source-filesystem/) ব্যবহার করা হয়েছে।

> কি কি প্লাগিন আপনি ব্যবহার করতে পারবেন জানতে [plugin library](/plugins) থেকে ঘুরে আসতে পারেন।

<EggheadEmbed
  lessonLink="https://egghead.io/lessons/gatsby-install-and-use-a-plugin-in-a-gatsby-site"
  lessonTitle="Install and use a plugin in a Gatsby site"
/>

### যা যা লাগবে

- একটি তৈরিকৃত [Gatsby সাইট](/docs/quick-start/) যাতে `gatsby-config.js` ফাইলটি আছে

### ধাপসমূহ

১. `gatsby-source-filesystem` প্লাগিনটি নিচের কমান্ডটি চালানোর মাধ্যমে ইন্সটল করুনঃ

```shell
npm install gatsby-source-filesystem
```

২. আপনার `gatsby-config.js` ফাইলে প্লাগিনটি সংযুক্ত করুন, এবং যা যা অপশন দরকার সেট করুন, ফাইল সিস্টেম সোর্স প্লাগিনটি একটি `name` এবং `path` অপশন হিসেবে গ্রহণ করেঃ

```javascript:title=gatsby-config.js
module.exports = {
  plugins: [
    // highlight-start
    {
      resolve: `gatsby-source-filesystem`,
      options: {
        name: `images`,
        path: `${__dirname}/src/images`,
      },
    },
    // highlight-end
  ],
}
```

_আপনি যেই প্লাগিনটি ব্যবহার করছেন তার README ফাইলের নির্দেশনাসমূহ আপনাকে কি কি অপশন লাগবে(যদি লাগে) তা জানতে সাহায্য করতে পারে। এই উদাহরণ আপনার সাইটে প্রভাব ফেলার জন্য আপনার একটি `src/images` ফোল্ডার তৈরি করতে হবে এবং এর ভেতর ফাইল রাখতে হবে।_

৩. `gatsby develop` রান করুন, আপনার প্লাগিন সাইট বিল্ড হওয়ার সাথে সাথে রান হবে।

### অতিরিক্ত রিসোর্স

- [আপনি সাইটে একটি প্লাগিন ব্যবহার করুন](/docs/using-a-plugin-in-your-site/) গাইডে অপশন কনফিগার করা এবং ডিফল্ট সেট করা সম্পর্কে আরও জানতে পারবেন।
- এই কনফিগারেশন ব্যবহার করে এমন একটি উদাহরণ Gatsby সাইট দেখতে [ডিফল্ট Gatsby স্টার্টার রিপোজিটরিটি](https://github.com/gatsbyjs/gatsby-starter-default/blob/master/gatsby-config.js) দেখতে পারেন।

## একটি প্লাগিন স্টার্টার ব্যবহার করে একটি প্লাগিন তৈরি করুন

আপনি যদি আপনার নিজের প্লাগিন তৈরি করতে চান তাহলে Gatsby প্লাগিন স্টার্টার ব্যবহার করে শুরু করতে পারেন।

### যা যা লাগবে

- একটি তৈরিকৃত [Gatsby সাইট](/docs/quick-start/) যাতে `gatsby-config.js` ফাইলটি আছে

### ধাপসমূহ

১. আপনার Gatsby সাইটের _বাইরে_ `gatsby new` কমান্ডের সাহায্যে স্টার্টারের উপর ভিত্তি করে একটি নতুন প্লাগিন তৈরি করুনঃ

```shell
gatsby new my-plugin https://github.com/gatsbyjs/gatsby-starter-plugin
```

আপনার ফোল্ডার স্ট্রাকচার দেখতে কিছুটা এমন হওয়া উচিতঃ

```text
gatsby-site
└── gatsby-config.js
└── src
    ├── components
    └── pages
my-plugin
├── gatsby-browser.js
├── gatsby-node.js
├── gatsby-ssr.js
├── index.js
└── package.json
```

২. আপনার সাইটের `gatsby-config.js` প্লাগিনটি সংযুক্ত করুন, আপনার লোকাল প্লাগিনের রুট ফোল্ডারের সাথে `require.resolve` এর মাধ্যমে লিংক করে। এই ক্ষেত্রে পাথ (অথবা প্লাগিনের নাম) আপনি প্লাগিন তৈরি করার সময় যে ফোল্ডারের নাম ব্যবহার করেছেন তার হতে হবে।

```javascript:title=gatsby-site/gatsby-config.js
module.exports = {
  plugins: [
    require.resolve(`../my-plugin), // highlight-line
  ],
}
```

৩. `gatsby develop` রান করুন। প্লাগিন স্টার্টারটি ঠিকমত আপনার সাইটে লোড হয়েছে নাকি যাচাই করার জন্য এটি `onPreInit` ধাপ শেষ হওয়ার পূর্বে কনসোলে "Loaded" একটি মেসেজ দেখাবেঃ

```shell
$ gatsby develop
success open and validate gatsby-configs - 0.033s
success load plugins - 0.074s
Loaded gatsby-starter-plugin
success onPreInit - 0.016s
...
```

৪. এখন আপনি [ব্রাউজার](/docs/browser-apis/), [সার্ভার-সাইড রেন্ডারিং](/docs/ssr-apis/), অথবা [নোড API-গুলো](/docs/node-apis/) ইমপ্লিমেন্ট করতে পারবেন এবং আপনার সাইট তা রান করবে যখনই আপনার প্লাগিন লোড হবে!

### অতিরিক্ত রিসোর্স

- ডেভেলপমেন্টে আপনার নিজের প্লাগিন তৈরি এবং লোড করার সম্পর্কে বিস্তারিত জানতে [একটি লোকাল প্লাগিন তৈরি করুন](/docs/creating-a-local-plugin/) গাইডটি দেখতে পারেন
