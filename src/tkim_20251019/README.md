# Buddyboddy Version of 2025.10.19 

## 1. Code architecture

~~~
/tkim~$ tree -L 3 tkim_20251019
tkim_20251019
├── App.vue
├── index.html
├── main.js
├── manifest.json
├── nim.js
├── package-lock.json
├── package-minimal.json
├── package.json
├── pages.json

├── pages
│   ├── NEUIKit
│   │   ├── App.vue
│   │   ├── components
│   │   ├── locale
│   │   ├── nim.js
│   │   ├── pages
│   │   ├── pages.json
│   │   ├── static
│   │   ├── tsconfig.json
│   │   ├── typings.d.ts
│   │   ├── uni.scss
│   │   └── utils
│   ├── index
│   │   └── index.vue
│   ├── redirect
│   │   ├── contact.vue
│   │   ├── conversation.vue
│   │   └── my.vue
│   └── test.vue

├── pages_chat_conversation
│   ├── NEUIKit
│   │   ├── App.vue
│   │   ├── components
│   │   ├── locale
│   │   ├── pages
│   │   ├── pages.json
│   │   ├── static
│   │   ├── tsconfig.json
│   │   ├── typings.d.ts
│   │   ├── uni.scss
│   │   └── utils
│   ├── conversation.vue
│   ├── index
│   │   └── index.vue
│   └── pages
│       └── redirect

├── pages_contact_user_team
│   ├── NEUIKit
│   │   ├── App.vue
│   │   ├── locale
│   │   ├── pages
│   │   ├── pages.json
│   │   ├── static
│   │   ├── tsconfig.json
│   │   ├── typings.d.ts
│   │   ├── uni.scss
│   │   └── utils
│   ├── contact.vue
│   ├── index
│   │   └── index.vue
│   ├── my.vue
│   └── pages
│       └── redirect

├── pages_vendor
│   └── package.json
├── static
│   ├── YX_IMG
│   │   ├── contact-selected.png
│   │   ├── contact.png
│   │   ├── conversation-selected.png
│   │   ├── conversation.png
│   │   ├── me-selected.png
│   │   └── me.png
│   └── logo.png

├── uni.promisify.adaptor.js
├── uni.scss
└── unpackage
    └── dist
        ├── build
        └── dev
~~~

## 2. Debugging

