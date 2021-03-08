# How to use this repo

This repository acts as both a tutorial and a development environment for custom
scripting in AEL's instance of Mozilla Hubs. You may fork the repo, add your own
scripts, and access them publicly through
[jsDelivr](https://www.jsdelivr.com/github).

[Click here](./tutorial/README.md) to start the tutorial!

# Structure

<pre>
<a href="./tutorial/">tutorial/</a> - How to create custom scripts
<a href="./src/">src/</a>
├─ <a href="./src/components/">components/</a> - A-Frame component definitions
├─ <a href="./src/entities/">entities/</a> - Sample glTF files from the Hubs Entity Generator
├─ <a href="./src/rooms/">rooms/</a> - Hubs room scripts
</pre>

# Development

After installing Node.js (and optionally `yarn`) run the following commands:

```bash
# 1. Install dependencies

yarn
# OR
npm install


# 2. Run development server

yarn start
# OR
npm start
```
