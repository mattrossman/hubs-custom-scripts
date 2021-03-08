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

# Visually Positioning Entities

Hard-coding properties like position, rotation, and scale can grow tiresome and
makes it difficult to contextualize where an entity lives in your scene. A
better approach is to position entities through a visual interface.

## Option 1: Hubs Entity Generator

Our [Hubs Entity Generator](https://www.aelatgt.org/hubs-entity-generator/) can
create a `.glb` file that contains arbitrary component data attached to an empty
object. This file can then be loaded into Spoke or directly into Hubs and
positioned just like a 3D model.

![Hubs Entity Generator application](https://i.imgur.com/ni5xPRW.png)

For complete instructions, refer to the project's
[README](https://github.com/aelatgt/hubs-entity-generator).

The [`3-entity-generator.js`](./src/rooms/3-entity-generator.js) and
[`4-root-component.js`](./src/rooms/4-root-component.js) scripts demonstrate two
ways of using the entity generator. The `entities` folder contains sample `.glb`
files that accompany these scripts. For instance, after loading
`3-entity-generator.js` into a room, you can drag `entity-3.glb` into the room
to make the entity appear.

We recommend following the pattern from
[`4-root-component.js`](./src/rooms/4-root-component.js) by writing a root
component for each entity that attaches all other components in its `init`
function. This way you can update the structure of your entity without needing
to export a new `.glb` file.

## Option 2: Hubs Blender Exporter

If you're already creating your scene in Blender, you can use the official
[Hubs Blender extension](https://github.com/MozillaReality/hubs-blender-exporter)
to attach components to objects in your Blender scene.

By default, only a few built-in components are provided. You can create your own
JSON config file to support custom components and their properties by following
the structure of the
[default config file](https://github.com/MozillaReality/hubs-blender-exporter/blob/master/default-config.json).
The config file can be swapped from the **Hubs** panel in the **Scene** tab of
Blender's sidebar.

![Annotated Blender sidebar](https://i.imgur.com/EvERDbj.png)
