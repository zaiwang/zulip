# Get stream ID

Get the unique ID of a given stream.

`GET {{ api_url }}/v1/get_stream_id`

## Usage examples

<div class="code-section" markdown="1">
<ul class="nav">
<li data-language="python">Python</li>
<li data-language="javascript">JavaScript</li>
<li data-language="curl">curl</li>
</ul>
<div class="blocks">

<div data-language="curl" markdown="1">

```
curl {{ api_url }}/v1/get_stream_id?stream=Denmark \
    -u BOT_EMAIL_ADDRESS:BOT_API_KEY
```
</div>

<div data-language="python" markdown="1">

```python
#!/usr/bin/env python

import zulip

# Download ~/zuliprc-dev from your dev server
client = zulip.Client(config_file="~/zuliprc-dev")

# Get the ID of a given stream
print(client.get_stream_id("Denmark"))
```
</div>

<div data-language="javascript" markdown="1">
More examples and documentation can be found [here](https://github.com/zulip/zulip-js).
```js
const zulip = require('zulip-js');

// Download zuliprc-dev from your dev server
const config = {
    zuliprc: 'zuliprc-dev',
};

zulip(config).then((client) => {
    // Get the ID of a given stream
    client.streams.getStreamId('Denmark').then(console.log);
});
```
</div>

</div>

</div>

## Arguments

**Note**: The following arguments are all URL query parameters.

{generate_api_arguments_table|arguments.json|get-stream-id.md}

## Response

#### Return values

* `stream_id`: The ID of the given stream.

#### Example response

A typical successful JSON response may look like:

```
{
    'stream_id':15,
    'result':'success',
    'msg':''
}
```

An example of a JSON response for when the supplied stream does not
exist:

```
{
    'code':'BAD_REQUEST',
    'msg':"Invalid stream name 'nonexistent'",
    'result':'error'
}
```

An example of a JSON response for when the `stream` query parameter is
not provided:

```
{
    "msg":"Missing 'stream' argument",
    "result":"error",
    "var_name":"stream",
    "code":"REQUEST_VARIABLE_MISSING"
}
```

{!invalid-api-key-json-response.md!}