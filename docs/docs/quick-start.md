---
title: জলদি শুরু করুন
---

এই অংশটি অভিজ্ঞ ডেভেলপারদের কথা মাথায় রেখে তৈরি করা হয়েছে। আরও বিস্তারিতভাবে Gatsby এর সাথে পরিচিত হওয়ার জন্য[আমাদের টিউটোরিয়াল দেখুন](/tutorial/)!

## Gatsby CLI ব্যবহার করুন

<EggheadEmbed
  lessonLink="https://egghead.io/lessons/gatsby-quick-start-with-gatsby-create-develop-and-build-gatsby-sites-from-the-command-line"
  lessonTitle="Quick Start with Gatsby: Create, Develop, and Build Gatsby Sites From the Command Line"
/>

**বিঃদ্রঃ**: এই ভিডিওতে `npx` ব্যবহার করা হয়েছে, যা npm এর কোন প্যাকেজ ইন্সটল না করেই ব্যবহার করার সুযোগ দেয়। `npx gatsby new` এই কমান্ডটি রান করা আর আপনার কম্পিউটারে gatsby-cli ইন্সটল করার পর `gatsby new` রান করা একই কথা।

### Gatsby CLI ইন্সটল করুন

```shell
npm install -g gatsby-cli
```

<<<<<<< HEAD
### একটি নতুন সাইট তৈরি করুন
=======
> The above command installs Gatsby CLI globally on your machine.

### Create a new site
>>>>>>> 90932a06db2e297cf416552b84e48b4b82e56fbc

```shell
gatsby new gatsby-site
```

### ডিরেক্টরি পরিবর্তন করে সাইট ফোল্ডারে যান

```shell
cd gatsby-site
```

### ডেভেলপমেন্ট সার্ভার চালু করুন

```shell
gatsby develop
```

<<<<<<< HEAD
Gatsby একটি হট-রিলোডিং ডেভেলপমেন্ট ইনভায়রনমেন্ট চালু করবে যা প্রাথমিকভাবে `localhost:8000` এই ঠিকানায় পাওয়া যায়।
=======
Gatsby will start a hot-reloading development environment accessible by default at `http://localhost:8000`.
>>>>>>> 90932a06db2e297cf416552b84e48b4b82e56fbc

`src/pages` এর জাভাস্ক্রিপ্ট পেইজগুলো এডিট করার চেষ্টা করে দেখুন। সেইভ করা পরিবর্তনগুলো সাথে সাথেই ব্রাউজারে দেখা যাবে।

### একটি প্রোডাকশন বিল্ড তৈরি করুন

```shell
gatsby build
```

Gatsby আপনার সাইটের জন্য স্ট্যাটিক HTML এবং প্রতি রুটের ভিত্তিতে জাভাস্ক্রিপ্ট কোড বান্ডেল করার মাধ্যমে আপনার জন্য একটি প্রোডাকশন বিল্ড তৈরি করবে।

### প্রোডাকশন বিল্ড লোকালি সার্ভ করুন

```shell
gatsby serve
```

Gatsby একটি লোকাল HTML সার্ভার চালু করে আপনার বিল্ড করা সাইট পরীক্ষা করে দেখার জন্য। এই কমান্ড রান করার পূর্বে `gatsby build` রান করতে ভুলবেন না।

### CLI কমান্ডগুলোর ডকুমেন্টেশন দেখুন

CLI কমান্ডগুলোর বিস্তারিত ডকুমেন্টেশন দেখতে টার্মিনালে `gatsby --help` রান করুন।

নির্দিষ্ট কোন কমান্ডের জন্য, `gatsby COMMAND_NAME --help` যেমনঃ `gatsby new --help` এভাবে রান করুন।

Gatsby CLI সম্পর্কে আরও বিস্তারিত জানতে ডকুমেন্টেশনের [CLI রেফারেন্স](/docs/gatsby-cli/) অংশটি দেখুন।
