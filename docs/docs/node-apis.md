---
title: Gatsby নোড এপিআই|
description: পেট তৈরির মতো সাধারণ ব্যবহারের জন্য Gatsby বিল্ড প্রক্রিয়াতে ব্যবহৃত নোড এপিআইগুলিতে ডকুমেন্টেশন|
jsdoc: ["gatsby/src/utils/api-node-docs.js"]
apiCalls: NodeAPI
---

Gatsby গ্রাফকিউল ডেটা স্তরে আপনার সাইটের ডেটা নিয়ন্ত্রণের জন্য প্লাগইন এবং সাইট নির্মাতাকে অনেকগুলি এপিআই দেয়|

## Async plugins

যদি আপনার প্লাগইন অ্যাসিঙ্ক অপারেশন করে (disk I/O, database access, calling remote APIs, etc.) আপনাকে হয় কোনও প্রতিশ্রুতি ফিরিয়ে দিতে হবে বা তৃতীয় যুক্তির সাথে প্রেরিত কলব্যাকটি ব্যবহার করতে হবে। Gatsby প্লাগইনগুলি কিছু API হিসাবে শেষ হয়ে গেলে, সঠিকভাবে কাজ করার জন্য, পূর্ববর্তী API গুলি প্রথমে সম্পূর্ণ হওয়া দরকার জানা| দেখা [Debugging Async Lifecycles](/docs/debugging-async-lifecycles/) আরও তথ্যের জন্য.

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

If your plugin does not do async work, you can just return directly.

## Usage

Implement any of these APIs by exporting them from a file named `gatsby-node.js` in the root of your project.
