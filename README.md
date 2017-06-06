# DiscordHandler

This class is using the integrated logging class from Python and [requests](http://docs.python-requests.org/en/master/) from PyPi. 

Feel free to change and add some good stuff.

## Requirements
Installing requests:
```
pip install requests
```

## Get Started:

First u need Discord or some Channels, where u have access to create a new Webhook.

You find Webhooks options in the channel settings. Create a new Webhook and copy the __Webhook url__. Note: Do NOT give this URL out to the public like me in previous commits. (I changed it :P )

## Exampel:
```python

    webhook_url = "Your Webhook here"
    agent = "My Application"

    logger = logging.getLogger("My Application")
    logger.setLevel(logging.DEBUG)

    # Create formatter
    FORMAT = logging.Formatter(
        "%(asctime)s - %(name)s - %(levelname)s - %(message)s")

    # Create DiscordHandler and StreamHandler
    discord_handler = DiscordHandler(webhook_url, agent)
    stream_handler = logging.StreamHandler()

    # Set log level to handlers
    discord_handler.setLevel(logging.WARNING)
    stream_handler.setLevel(logging.DEBUG)

    # Add format to handlers
    discord_handler.setFormatter(FORMAT)
    stream_handler.setFormatter(FORMAT)

    # Add the handlers to the Logger
    logger.addHandler(discord_handler)
    logger.addHandler(stream_handler)

    logger.debug("Logger created")
```

For more Infos: [Logging Cookbook](https://docs.python.org/3/howto/logging-cookbook.html)
