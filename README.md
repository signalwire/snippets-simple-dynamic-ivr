# Snippets Simple Dynamic IVR
This snippet will show you how to implement dyanmic interactive voice reponse menu.
## About Simple Dynamic IVR
Create menu trees easily and dynamically with a simple json object.
## Getting Started
You will need a machine with Python installed, the SignalWire SDK, a provisioned SignalWire phone number, and optionaly Docker if you decide to run it in a container.

For this demo we will be using Python, but more languages may become available.

- [x] Python
- [x] SignalWire SDK
- [x] SignalWire Phone Number
- [x] Docker (Optional)
----
## Running Simple Dynamic IVR - How It Works
## Methods and Endpoints

```
Endpoint: /get_menu
Methods: GET OR POST
Requests generate a menu, it will default to main menu if no menu is specified.  The get_menu, will look for dtmf entries to select action for routing and moving along a menu tree.
```

```
Endpoint: /get_voicemail
Methods: GET OR POST
Requests to get_voicemail, produce a LaML Voice response to simulate an endpoint.
```
## Setup Your Menus
1. Edit the menus.json file

This example file has 3 menus
Each menu contains a index, which is equal to the keypress on the menu, a verbiage, and an action
```javascript
{
  "main": {
    "1": {
      "verbiage": "For sales press 1",
      "action": "/get_menu?menu=sales"
    },
    "2": {
      "verbiage": "For tech support press 2",
      "action": "/get_menu?menu=tech"
    }
  },
  "sales": {
    "1": {
      "verbiage": "For partners, press 1",
      "action": "/get_voicemail?group=sale_partners"
    },
    "2": {
      "verbiage": "For assistance with a purchase, press 2",
      "action": "/get_voicemail?group=sale_support"
    }
  },
  "tech": {
    "1": {
      "verbiage": "For issues with your internet, press 1",
      "action": "/get_voicemail?group=internet_support"
    },
    "2": {
      "verbiage": "For issues with your cell phone, press 2",
      "action": "/get_voicemail?group=mobile_support"
    }
  }
}

```

## Setup Your Enviroment File

1. Copy from example.env and fill in your values
2. Save new file callled .env

Your file should look something like this
```
## This is the full name of your SignalWire Space. e.g.: example.signalwire.com
SIGNALWIRE_SPACE=
# Your Project ID - you can find it on the `API` page in your Dashboard.
SIGNALWIRE_PROJECT=
# Your API token - you can generate one on the `API` page in your Dashboard
SIGNALWIRE_TOKEN=
# The phone number you'll be using for this Snippets. Must include the `+1` , e$
SIGNALWIRE_NUMBER=
# Hostname
HOSTNAME=

```

## Build and Run on Docker
Lets get started!
1. Use our pre-built image from Docker Hub 
```
For Python:
docker pull signalwire/snippets-simple-dynamic-ivr:python
```
(or build your own image)

1. Build your image
```
docker build -t snippets-simple-dynamic-ivr .
```
2. Run your image
```
docker run --publish 5000:5000 --env-file .env snippets-simple-dynamic-ivr
```
3. The application will run on port 5000

## Build and Run Natively
For Python
```
1. Replace environment variables
2. From command line run, python3 app.py
```

----
# More Documentation
You can find more documentation on LaML, Relay, and all Signalwire APIs at:
- [SignalWire Python SDK](https://github.com/signalwire/signalwire-python)
- [SignalWire API Docs](https://docs.signalwire.com)
- [SignalWire Github](https://gituhb.com/signalwire)
- [Docker - Getting Started](https://docs.docker.com/get-started/)
- [Python - Gettings Started](https://docs.python.org/3/using/index.html)

# Support
If you have any issues or want to engage further about this Signal, please [open an issue on this repo](../../issues) or join our fantastic [Slack community](https://signalwire.community) and chat with others in the SignalWire community!

If you need assistance or support with your SignalWire services please file a support ticket from your Dashboard. 

