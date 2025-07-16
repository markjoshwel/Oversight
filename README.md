# Oversight

an importance-triaging message forwarder to live simply, named after
[Tom Scott's eponymous video on a civil surveillance system](https://www.youtube.com/watch?v=RIuf1V1FhpY)

largely inspired by Ben Vallack's
["Solving the 'Perfect Dumbphone' Problem"](https://www.youtube.com/watch?v=qKFrwX-r2Uk)
video. in the video, he uses a locally ran Large Language Model to triage messages for
importance, and then sends back a message to the sender for them to call him
instead as he has call forwarding enabled. (and also partly inspired by Ljot
Swanhild's ["the process of disconnecting"](https://www.youtube.com/watch?v=JiT7MFoo8eE))

## an overview

Oversight:

1. receives a message

2. sends it to a locally-hosted LLM to triage
    - if it is certain it is unimportant, do nothing (for now)
    - if it is possibly important, continue

3. process it into SMS-chunkable messages with
    any sensitive information redacted, or default to something like
  
    `"<Name> sent you a message on <Platform>"`

4. reply back to the sender with a template message such as

    `"(Automated) This seems important. I may not be on my phone or computer
    at the moment, if this is time-sensitive, please call me via my number on
    your phone app."`

alongside this, there is also:

- an encrypted web interface
  - listing real time incoming messages from all platforms with notification
    toasts (i access this via Tailscale)
  - search engine for all stored messages
  - listing main and subsystem logs

**at no stage** does the LLM respond on my behalf. any uncertainty in triaging
will forward a summary or notice for the user to decide with context and reply to
