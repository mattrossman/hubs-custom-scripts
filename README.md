# How to use this repo

This repository acts as both a tutorial and a development environment for custom
scripting in AEL's instance of Mozilla Hubs. You may fork the repo, add your own
scripts, and access them publicly through
[jsDelivr](https://www.jsdelivr.com/github).

[Click here](./tutorial/README.md) to start the tutorial!

# Structure

```
tutorial/ - How to create custom scripts
src/
├─ components/ - A-Frame component definitions
├─ entities/ - Sample glTF files from the Hubs Entity Generator
├─ rooms/ - Hubs room scripts

```

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
