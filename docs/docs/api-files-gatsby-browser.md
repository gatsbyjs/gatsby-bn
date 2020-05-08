---
title: gatsby-browser.js API ফাইল
---

`gatsby-browser.js` ফাইলটি আপনাকে ব্রাউজারের ভেতর বিভিন্ন একশনের প্রতিক্রিয়া সম্পাদন করতে, এবং আপনার সাইটকে অতিরিক্ত কম্পোনেন্টের ভেতর আবদ্ধ করতে সাহায্য করে। [Gatsby ব্রাউজার API](/docs/browser-apis) আপনাকে Gatsby-এর [ক্লায়েন্ট-সাইডের](/docs/glossary#client-side) সাথে যোগাযোগ রাখতে বিভিন্ন অপশন প্রদান করে।

`wrapPageElement` এবং `wrapRootElement` API-গুলো ব্রাউজার এবং [সার্ভার-সাইড রেন্ডারিং (SSR)](/docs/ssr-apis) উভয় API তেই পাওয়া যায়। আপনি যদি এদের মধ্যে কোনটি ব্যবহার করে থাকেন, তাহলে `gatsby-ssr.js` এবং `gatsby-browser.js` দুই জায়গাতেই ইমপ্লিমেন্ট করবেন নাকি বিবেচনা করে দেখুন যাতে SSR এবং Node.js এর মাধ্যমে তৈরিকৃত পেইজগুলো এবং ব্রাউজার জাভাস্ক্রিপ্টের মাধ্যমে [হাইড্রেটকৃত](/docs/glossary#hydration) পেইজগুলো একই হয়।

ব্রাউজার API-গুলো ব্যবহার করার জন্য আপনার সাইটের রুটে `gatsby-browser.js` নামের একটি ফাইল তৈরি করুন। এই ফাইল থেকে যেই API-গুলো ব্যবহার করতে চান তা এক্সপোর্ট করুন।

```jsx:title=gatsby-browser.js
const React = require("react")
const Layout = require("./src/components/layout")

// ক্লায়েন্ট রাউট পরিবর্তন হলে লগ করে
exports.onRouteUpdate = ({ location, prevLocation }) => {
  console.log("new pathname", location.pathname)
  console.log("old pathname", prevLocation ? prevLocation.pathname : null)
}

// সবগুলো পেইজকে একটি কম্পোনেন্টে আবদ্ধ করে
exports.wrapPageElement = ({ element, props }) => {
  return <Layout {...props}>{element}</Layout>
}
```
