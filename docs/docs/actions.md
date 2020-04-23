---
title: একশন
description: একশন সম্পর্কিত ডকুমেন্টেশন এবং কিভাবে এগুলো Gatsby এর অভ্যন্তরীণ স্টেটে পরিবর্তন আনতে সাহায্য করে
jsdoc:
  - "gatsby/src/redux/actions/public.js"
  - "gatsby/src/redux/actions/restricted.js"
contentsHeading: Functions
---

Gatsby অভ্যন্তরীণভাবে স্টেট ম্যানেজ করার জন্য [Redux](http://redux.js.org) ব্যবহার করে। আপনি যখন কোন Gatsby API ইমপ্লিমেন্ট করেন, তখন আপনাকে কিছু একশন পাস করা হয়(Redux এ [bindActionCreators](https://redux.js.org/api/bindactioncreators/) দ্বারা বাইন্ড করা একশনগুলোর মত) যেগুলো ব্যবহার করে আপনি আপনার সাইটের স্টেট পরিবর্তন করতে পারেন।

`actions` অবজেক্ট এই ফাংশনগুলো ধারণ করে এবং এদেরকে আলাদাভাবে ES6 অবজেক্ট ডি-স্ট্রাকচারিং এর মাধ্যমে বের করে আনা যায়।

```javascript
// createNodeField ফাংশনের জন্য
exports.onCreateNode = ({ node, getNode, actions }) => {
  const { createNodeField } = actions
}
```
