---
sidebar_position: 1
---

# Tutorial Intro

유니티의 세계에 온걸 환영합니다. 일단 코딩을 하기에 앞서 유니티는 C# 언어로 돌아갑니다.

### What you'll need

- [Node.js](https://nodejs.org/en/download/) version 16.14 or above: <-- 아마 이거 깔고 하면 사이트 만들수 있음
  - When installing Node.js, you are recommended to check all checkboxes related to dependencies.

## Generate a new site

Generate a new Docusaurus site using the **classic template**.

The classic template will automatically be added to your project after you run the command:

```bash
npm init docusaurus@latest my-website classic
```

You can type this command into Command Prompt, Powershell, Terminal, or any other integrated terminal of your code editor.

The command also installs all necessary dependencies you need to run Docusaurus.

## Start your site

Run the development server:

```bash
cd my-website
npm run start
```

The `cd` command changes the directory you're working with. In order to work with your newly created Docusaurus site, you'll need to navigate the terminal there.

The `npm run start` command builds your website locally and serves it through a development server, ready for you to view at http://localhost:3000/.

Open `docs/intro.md` (this page) and edit some lines: the site **reloads automatically** and displays your changes.
