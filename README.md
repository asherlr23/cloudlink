![CLOUDLINK 4 BANNER](https://user-images.githubusercontent.com/12957745/188282246-a221e66a-5d8a-4516-9ae2-79212b745d91.png)

# Cloudlink v0.2.0
CloudLink is a free and open-source websocket solution optimized for Scratch.
Originally created as a cloud variables alternative, it can function as a multi-purpose websocket framework for other projects.
**THIS VERSION OF CLOUDLINK IS STILL UNDER DEVELOPMENT. DO NOT USE IN A PRODUCTION ENVIRONMENT.**

# 💡 Features 💡

### 🪶 Fast and lightweight 
CloudLink can run on minimal resources. At least 25MB of RAM and any reasonably capable CPU can run a CloudLink server.

### 🌐 Essential networking tools
* Unicast and multicast packets across clients
* Expandable functionality with a built-in method loader
* Support for bridging servers
* Admin functionality for management

### 📦 Minimal dependencies
All dependencies below can be installed using `pip install -r requirements.txt`.
* 🐍 Python >=3.11
* 🧵 asyncio (Built-in)
* 📃 ["ujson" ultrajson](https://github.com/ultrajson/ultrajson)
* 🔍 [pyeve/cerberus](https://github.com/pyeve/cerberus)
* ❄️ ["snowflake-id" vd2org/snowflake](https://github.com/vd2org/snowflake)
* 🌐 [aaugustin/websockets](https://github.com/aaugustin/websockets)

### 🔋Batteries included
The CloudLink Python server comes with full support for the CL4 protocol and the Scratch cloud variable protocol.
Just download, setup, and start!

### 🧱 Plug-and-play modularity
You can easily extend the functionality of the server using classes and decorators. 
Here's an example of a simple plugin that displays "Foobar!" in the console
when a client sends the message `{ "cmd": "foo" }` to the server.

```python
# Import the server
from cloudlink import server

# Instanciate the server object
cl = server()

# Set logging level
cl.logging.basicConfig(
    level=cl.logging.DEBUG
)

# Define the functions your plugin executes
class myplugin:
	def __init__(self, server):
        
        # Example command - client sends { "cmd": "foo" } to the server, this function will execute
		@server.on_command(cmd="foo", schema=cl.schemas.clpv4)
		async def foobar(client, message):
			print("Foobar!")

# Load the plugin!
myplugin(cl)

# Start the server!
cl.run()
```

# 🐈 A powerful extension for Scratch 3.0
You can learn about the protocol using the original Scratch 3.0 client extension.
Feel free to test-drive the extension in any of these Scratch mods:

- [TurboWarp](https://turbowarp.org/editor?extension=https://extensions.turbowarp.org/cloudlink.js)
- [SheepTester's E 羊 icques](https://sheeptester.github.io/scratch-gui/?url=https://mikedev101.github.io/cloudlink/S4-0-nosuite.js)
- [Ogadaki's Adacraft](https://adacraft.org/studio/)
- [Ogadaki's Adacraft (Beta)](https://beta.adacraft.org/studio/)

# 📃 The CloudLink Protocol 📃
You can learn more about the CloudLink protocol on [CL's official HackMD documentation page.](https://hackmd.io/g6BogABhT6ux1GA2oqaOXA)
