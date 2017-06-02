![logo](https://raw.githubusercontent.com/unifiedstreaming/origin/master/unifiedstreaming-logo-black.jpg)


Live Origin
-----------
This image can be used as a Live streaming Origin for a single channel.


What is Unified Origin?
-----------------------
Unified Origin offers one solution for just-in-time packaging to MPEG-DASH, Apple (HLS), Adobe (HDS) and Microsoft (MSS). Our added features include content protection, restart TV, time-shift, catchup-TV, subtitles, and multiple language and audio tracks.

Further documentation is available at: <http://docs.unified-streaming.com>

Usage
-----
This image is usable out of the box, but must be configured using environment variables.

Available variables are:

|Variable        |Usage   |Mandatory?|
|----------------|--------|----------|
|USP_LICENSE_KEY |Your license key. To evaluate the software you can create an account at <https://private.unified-streaming.com/register/>|Yes|
|CHANNEL|Channel name, the publishing point URL will be http://<container\>/CHANNEL/CHANNEL.isml|Yes|
|PUB_POINT_OPTS  |Options to use when creating the publishing point. See http://docs.unified-streaming.com/faqs/general/options.html|No|
|LOG_LEVEL|Sets the Apache error log level|No|
|LOG_FORMAT|Sets a custom Apache log format|No|


More detailed documentation is available at: <http://docs.unified-streaming.com/documentation/live/index.html>

Example
-------
A simple example, running locally on port 1080 with a channel named test01:

```bash
docker run \
  -e USP_LICENSE_KEY=<license_key> \
  -e CHANNEL=test01 \
  -p 1080:80 \
  unifiedstreaming/live:1.7.28
```

The publishing point will be created at <http://localhost:1080/test01/test01.isml>.
Its state can be checked by running:

```bash
curl http://localhost:1080/test01/test01.isml/state
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- Created with Unified Streaming Platform(version=1.7.28) -->
<smil
  xmlns="http://www.w3.org/2001/SMIL20/Language">
  <head>
    <meta
      name="updated"
      content="2017-06-02T11:32:42.026883Z">
    </meta>
    <meta
      name="state"
      content="idle">
    </meta>
  </head>
</smil>
```