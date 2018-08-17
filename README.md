# Cobwebhook

Set of plugs that do authentication for various services.

## API

Use as a part of Plug pipeline:

```
defmodule Pipeline do
  use Plug.Builder

  def secrets do
   ["1cb606ad1ccf30f99f60c8bc1d0bfec9"]
  end

  plug Cobwebhook.Slack, &__MODULE__.secrets/0
  plug Webhook
end
```

Takes a function that returns a  list of valid secrets. On valid request, sets
`conn.assigns.secret` and forwards request to the next plug in the pipeline.
