---
title: API ফাইল
---

Gatsby ৪টি ফাইল ব্যবহার করে আপনার সাইট সজ্জিত এবং এর আচরণ নিয়ন্ত্রণ করতে, যা আপনার প্রজেক্তের মূলে অবস্থিত। এই ফাইলগুলো ঐচ্ছিক।

- [gatsby-config.js](/docs/api-files-gatsby-config) - Plugin সক্রিয় করে, সাধারণ সাইট তথ্য সংজ্ঞায়িত করে এবং অন্যান্য সাইট সম্পর্কিত তথ্য সংরক্ষণ করে যা Gatsby এর GraphQL তথ্যের স্তরের সাথে সংযোজিত করে।
- [gatsby-browser.js](/docs/api-files-gatsby-browser) - Gives you control over Gatsby's behavior in the browser. For example, responding to a user changing routes, or calling a function when the user first opens any page.
- [gatsby-node.js](/docs/api-files-gatsby-node) - Allows you to respond to events in the Gatsby build cycle. For example, adding pages dynamically, editing GraphQL nodes as they are created, or performing an action after a build is complete.
- [gatsby-ssr.js](/docs/api-files-gatsby-ssr) - Exposes Gatsby's server-side rendering process so you can control how it builds your HTML pages.
