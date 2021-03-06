---
title: Node ইন্টারফেস
---

"node" গ্যাটসবির ডেটা সিস্টেমের কেন্দ্র। গ্যাটসবিতে যুক্ত করা সমস্ত ডেটা
নোড ব্যবহার করে মডেল করা হয়েছে।

## নোড ডেটা স্ট্রাকচার 

বেসিক নোড ডেটা স্ট্রাকচারটি নিম্নরূপ:

```flow
id: String,
children: Array[String],
parent: String,
fields: Object,
internal: {
  contentDigest: String,
  mediaType: String,
  type: String,
  owner: String,
  fieldOwners: Object,
  content: String,
}
...other fields specific to this type of node
```

### `parent`

অন্য নোডগুলি প্রসারিত করতে ইচ্ছুক এমন প্লাগইনগুলির জন্য সংরক্ষিত একটি key।

### `contentDigest`

এই নোডের সামগ্রীর একটি ডাইজেস্ট "Hash" বা সংক্ষিপ্ত ডিজিটাল সারাংশ (যেমন, `md5sum`)|

ডাইজেস্ট এই নোডের বিষয়বস্তুর সাথে অনন্য হওয়া উচিত কারণ এটি ক্যাশিং-এর জন্য ব্যবহৃত হয়। যদি বিষয়বস্তু পরিবর্তন হয় তবে এই ডাইজেস্টও পরিবর্তন করা উচিত| এখানে একটি `md5` নামের ডাইজেস্ট তৈরি করার জন্য [createContentDigest](https://github.com/gatsbyjs/gatsby/blob/master/packages/gatsby-core-utils/src/create-content-digest.js) নামের একটি সহায়ক ফাংশন রয়েছে|

### `mediaType`

 অপ্শনাল [media type](https://en.wikipedia.org/wiki/Media_type) যে ট্রান্সফর্মার প্লাগইনগুলিতে ইঙ্গিত করতে পারে যে এই নোডে আরও এমন ডেটা রয়েছে যার ওপর তারা প্রক্রিয়া করতে পারে।

### `type`

প্লাগইন ওনার দ্বারা নির্বাচিত একটি গ্লোবালি অনন্য নোড টাইপ।

### `owner`

এই নোডটি তৈরি করে এমন প্লাগইন| এই ক্ষেত্রটি গ্যাটসবির দ্বারাই যুক্ত হয় (এবং প্লাগইন দ্বারা নয়)|

### `fieldOwners`

কোন প্লাগইনগুলি কোন ক্ষেত্র তৈরি করেছে তা স্টোর করে| এই ক্ষেত্রটি গ্যাটসবির দ্বারাই যুক্ত হয় (এবং প্লাগইন দ্বারা নয়)|

### `content`

অপ্শনাল ক্ষেত্র যা ট্রান্সফর্মার প্লাগইনগুলি নিতে এবং আরও প্রক্রিয়া করতে পারে এমন নোডের raw কনটেন্ট উন্মুক্ত করে।

## সোর্স প্লাগিন সমূহ

গ্যাটসবিতে নতুন নোড "সোর্স" প্লাগইনগুলি দ্বারা যুক্ত করা হয়. একটি প্রচলিত "সোর্স" প্লাগইন যা অনেক গ্যাটসবি
সাইট দ্বারা ব্যবহৃত হয় সেটা হলো [ফাইল সিস্টেম সোর্স প্লাগিন](/packages/gatsby-source-filesystem/)
যা ডিস্ক--এর ফাইলগুলিকে ফাইল নোডে রূপান্তরিত করে|

অন্যান্য সোর্স প্লাগিন বাহ্যিক এপিআই থেকে ডেটা টানে, যেমন
[Drupal](/packages/gatsby-source-drupal/) আর
[Hacker News](/packages/gatsby-source-hacker-news/)

## ট্রান্সফরমার প্লাগিন সমূহ

ট্রান্সফর্মার প্লাগইনগুলি সোর্স নোডগুলিকে রূপান্তর করে নতুন ধরণের নোড তৈরি করতে পারে|
গ্যাটসবি সাইট তৈরি করার সময় সোর্স প্লাগিন সমূহ আর ট্রান্সফরমার প্লাগিন সমূহ 
উভয়কেই ইনস্টল করা খুব প্রচলিত|

ট্রান্সফর্মার প্লাগইনগুলির দ্বারা তৈরি নোডগুলি তাদের "parent"-এর 
"child" হিসাবে সেট করা হয়|

- [Remark (মার্কডাউন লাইব্রেরি) ট্রান্সফরমার প্লাগিন](/packages/gatsby-transformer-remark/)
  `mediaType` ও `text/markdown` দিয়ে বানানো নতুন নোড-এর খোঁজ করে 
  এবং সেই নোডগুলিকে `html` ক্ষেত্র-সমেত `MarkdownRemark` নোড সমূহে 
  রূপান্তর করে|
- [YAML ট্রান্সফরমার প্লাগিন](/packages/gatsby-transformer-yaml/) 
`text/yaml` মিডিয়া টাইপ সমেত নতুন নোড (যেমন, একটি `.yaml` ফাইল)-এর খোঁজ করে 
এবং YAML সোর্স-কে জাভাস্ক্রিপ্ট অবজেক্টে পার্স করে নতুন YAML চাইল্ড নোড তৈরী করে|

## GraphQL

গ্যাটসবি স্বয়ংক্রিয়ভাবে আপনার সাইটের নোড স্ট্রাকচার অনুমান করে এবং একটি GraphQL স্কিমা তৈরি করে
যা আপনি আপনার সাইটের কম্পোনেন্ট-গুলির থেকে কোয়েরি করতে পারেন।

## নোড ক্রিয়েশন

নোড কীভাবে তৈরি এবং একসাথে লিঙ্ক করা হয় সে সম্পর্কে আরও জানার জন্য, [নোড ক্রিয়েশন](/docs/node-creation/) ডকুমেন্টেশন-এর "Behind the Scenes" অধ্যায় দেখুন|
