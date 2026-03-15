# Aurelia Craft — Website

বাংলাদেশের নারীদের জন্য প্রিমিয়াম থ্রি-পিস ও শাড়ির কালেকশন।

**Live:** https://faisalnabil.github.io/aurelia-craft/

---

## নতুন পণ্য যোগ করবেন কীভাবে

### ১. ছবি যোগ করুন
`public/images/` ফোল্ডারে পণ্যের ছবি রাখুন।
- ফরম্যাট: JPG বা PNG
- নাম: ছোট হাতে, space-এর বদলে hyphen ব্যবহার করুন
- যেমন: `joypuri-navy-pink.jpg`

### ২. Product data আপডেট করুন
`src/data/products.js` ফাইলে নতুন object যোগ করুন:

```js
{
  slug: 'my-new-product',           // URL হবে /products/my-new-product
  name: 'পণ্যের নাম',
  subtitle: 'সাব-টাইটেল',
  category: 'threepiece',           // threepiece অথবা saree
  badge: 'নতুন',                    // নতুন | জনপ্রিয় | লিমিটেড | ''
  price: 1200,
  image: 'my-new-product.jpg',      // public/images/ এ রাখা ছবি
  fabric: 'সফট কটন',
  design: 'ব্লক প্রিন্ট',
  occasion: 'ঈদ, উৎসব',
  description: 'বিস্তারিত বিবরণ...',
  details: [
    'পয়েন্ট ১',
    'পয়েন্ট ২',
  ],
  related: ['joypuri-navy-pink'],   // সম্পর্কিত পণ্যের slug
},
```

### ৩. GitHub-এ push করুন
```bash
git add .
git commit -m "নতুন পণ্য: পণ্যের নাম"
git push
```

GitHub Actions automatically build ও deploy করবে। ২–৩ মিনিটে live!

---

## Facebook post-এ share করার link format
```
https://faisalnabil.github.io/aurelia-craft/products/PRODUCT-SLUG/
```

যেমন:
- `https://faisalnabil.github.io/aurelia-craft/products/joypuri-navy-pink/`
- `https://faisalnabil.github.io/aurelia-craft/products/joypuri-olive/`

---

## Local development

```bash
npm install
npm run dev
```

## Built with
- [Astro](https://astro.build) — Static site generator
- GitHub Pages — Free hosting
- GitHub Actions — Auto deploy
