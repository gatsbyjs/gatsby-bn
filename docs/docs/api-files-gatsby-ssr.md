---
title: gatsby-ssr.js API ফাইল
---

`gatsby-ssr.js` ফাইলটি আপনাকে স্ট্যাটিক HTML ফাইলের কন্টেন্ট পরিবর্তন করতে সহায়তা করে যখন এটি Gatsby এবং Node.js দ্বারা সার্ভার-সাইডে রেন্ডার(SSR) হয়। [Gatsby SSR API-সমূহ](/docs/ssr-apis/) ব্যবহার করার জন্য, আপনার সাইটের রুটে `gatsby-ssr.js` নামের একটি ফাইল তৈরি করুন। আপনি যেই API-গুলো ব্যবহার করতে চান তা এই ফাইলে এক্সপোর্ট করুন।

`wrapPageElement` এবং `wrapRootElement` API-গুলো SSR এবং [ব্রাউজার](/docs/browser-apis) উভয় API তেই পাওয়া যায়। আপনি যদি এদের মধ্যে কোনো একটি ব্যবহার করে থাকেন, তাহলে `gatsby-ssr.js` এবং `gatsby-browser.js` দুই জায়গাতেই ইমপ্লিমেন্ট করবেন নাকি বিবেচনা করে দেখুন যাতে SSR এবং Node.js এর মাধ্যমে তৈরিকৃত পেইজগুলো এবং ব্রাউজার জাভাস্ক্রিপ্টের মাধ্যমে [হাইড্রেটকৃত](/docs/glossary#hydration) পেইজগুলো একই হয়।

```jsx:title=gatsby-ssr.js
const React = require("react")
const Layout = require("./src/components/layout")

// body element এ একটি ক্লাস সংযুক্ত করে
exports.onRenderBody = ({ setBodyAttributes }, pluginOptions) => {
  setBodyAttributes({
    className: "my-body-class",
  })
}

// সবগুলো পেইজকে একটি কম্পোনেন্টে আবদ্ধ করে
exports.wrapPageElement = ({ element, props }) => {
  return <Layout {...props}>{element}</Layout>
}
```
