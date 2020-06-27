---
title: Gatsby নোড APIs
description: পেজ তৈরির মতো সাধারণ ব্যবহারের জন্য Gatsby বিল্ড প্রক্রিয়াতে ব্যবহৃত নোড APIs ডকুমেন্টেশন
jsdoc: ["gatsby/src/utils/api-node-docs.js"]
apiCalls: NodeAPI
---

Gatsby GraphQL ডেটা স্তরে আপনার সাইটের ডেটা নিয়ন্ত্রণের জন্য প্লাগইন এবং সাইট নির্মাতাকে অনেকগুলি API দেয়।

## Async plugins

যদি আপনার প্লাগইন async অপারেশন সম্পাদন করে (disk I/O, database access, calling remote APIs, etc.) আপনাকে হয় কোনও promise ফিরিয়ে দিতে হবে বা তৃতীয় আর্গুমেন্টের সাথে প্রেরিত কলব্যাকটি ব্যবহার করতে হবে। Gatsby প্লাগইনগুলি কিছু APIs হিসাবে শেষ হয়ে গেলে, সঠিকভাবে কাজ করার জন্য, পূর্ববর্তী API গুলি প্রথমে সম্পূর্ণ হওয়া দরকার জানা। দেখা [Debugging Async Lifecycles](/docs/debugging-async-lifecycles/) আরও তথ্যের জন্য।

```javascript
// Promise API
exports.createPages = () => {
  return new Promise((resolve, reject) => {
    // do async work
  })
}

// Callback API
exports.createPages = (_, pluginOptions, cb) => {
  // do Async work
  cb()
}
```

যদি আপনার প্লাগইন async কাজ না করে তবে আপনি সরাসরি সরাসরি ফিরে আসতে পারেন।

## ব্যবহার

এই API গুলোর যেকোনোটিই আপনি `gatsby-node.js` নামের ফাইল থেকে এক্সপোর্ট করে আপনার রুট প্রজেক্টে ইমপ্লিমেন্ট করতে পারেন।
