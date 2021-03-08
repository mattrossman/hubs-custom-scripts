# How to use this repo

This repository acts as both a tutorial and a development environment for custom
scripting in AEL's instance of Mozilla Hubs. To get started,
[create a repository from this template](https://github.com/mattrossman/hubs-custom-scripts/generate)
and follow the guide below. You can then add new components and room scripts to
the existing structure, or create your own development environment.

# Structure

<pre>
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

This will start a static file server on port 1234 that serves files in the
`/src` directory. Additionally, it will connect this server to
[Ngrok](https://ngrok.io) so it will be accessible from outside your local
network.

# Adding Scripts to Hubs

The Hubs client hosted on [hubs.aelatgt.net](https://hubs.aelatgt.net) has been
modified to support attaching custom scripts to each room. These scripts will
execute during the page load sequence before connecting to the networked scene.
This allows you to add new forms of interactivity to Hubs without needing to
build the client from source.

## Instructions

1. Click the hamburger menu in the top-left
2. Select **Room Settings**
3. At the bottom of the room settings dialog box, paste the public URL to a
   script
4. Click **add** to append this URL to the list of scripts
5. Click **Apply** to save the room settings
6. Refresh the page to see the effects of the script(s)

![Screenshot of custom script input field](https://i.imgur.com/j6IrzWH.png)

## Try it!

Create a new room from the
[Wide Open Space](https://hubs.aelatgt.net/scenes/BNKgTxW/wideopenspace) scene.
We recommend testing with this scene since it spawns you near the world origin.

Start the development server and visit the public URL for the `rooms` folder
that's printed to the console. This page shows a listing of each of your room
scripts. Copy the URL for the `1-basic.js` room script and paste it into the
room settings as described above.

Refresh the page and you should see a red box appear near the center of the
room:

![Red box floating above the ground](https://i.imgur.com/a73GkTV.png)

Take a look at the [`1-basic.js`](./src/rooms/1-basic.js) script to understand
how it works. This file uses basic JavaScript and DOM APIs to construct an
A-Frame entity, give it properties, and add it to the scene. Refer to the
[A-Frame documentation](https://aframe.io/docs/1.2.0/introduction/javascript-events-dom-apis.html#modifying-the-a-frame-scene-graph)
on this topic to learn more.

# Custom Components

Anything you can do in a regular A-Frame scene will work in Hubs, including
adding custom components. Refer to the A-Frame
[component documentation](https://aframe.io/docs/1.2.0/core/component.html) to
learn more about this process.

The [`2-custom-component.js`](./src/rooms/2-custom-component.js) room script
shows an example of a custom component that attaches a
`THREE.MeshNormalMaterial` to an entity. Notice that we store each component
definition in a separate file inside the `components` folder and import them
into the room script. This pattern allows us to write multiple room scripts that
use the same component.
