# Websocket Example

This is an example of integrating with [Ultravox](https://ultravox.ai) using a websocket connection in Python. It uses the `websockets` library from PyPI.

See [the documentation](https://docs.ultravox.ai) for more information, such as other kinds of data messages that can be sent and received.

## Running

This example project uses [uv](https://github.com/astral-sh/uv) for package management and tooling.  Once you have uv installed, you can format and lint code with ruff (`uv run ruff format` to format, `uv run ruff check --fix` to lint) or run the example.

```bash
export ULTRAVOX_API_KEY=<your_key>
uv run websocket_client.py
```

You can use `uv run websocket_client.py --help` to see various command-line options this example supports. By default you'll be talking to a "Dr. Donut" drive-thru attendant, but you can alter the system prompt as you like.

Note that the first time you run the example, uv will set up a new python enviornment and install relevant dependencies.

## Notes

* User audio is constantly streamed (in its own task).
* The example uses 48kHz audio for input and output, though this is configurable.
* The example handles PlaybackClearBuffer messages so that 30s of audio can be buffered on the client without impacting interruptions.
* The example adds an `apiVersion` query parameter in the url. This parameter is optional as there is currently only one version of the API (version 1).
* This example ignores user transcripts and doesn't handle agent transcripts robustly. See [the webRTC client SDK](https://github.com/fixie-ai/ultravox-client-sdk-python/blob/7b9cf372c0bdc75657c398e4bbf44cebed2cf8b0/ultravox-client/ultravox_client/session.py#L381) for an example of more complete handling.
