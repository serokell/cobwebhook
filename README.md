# Cobwebhook

Cobwebhook is a small elixir library that provides plugs which handle
authentication and payload processing for various services.

## Build Instructions

You can add this library to your project dependencies in `mix.exs` with e.g.:

```elixir
def deps do
  [{:cobwebhook, "~> 0.4.0"}]
end
```

Then, run `mix deps.get` to update your dependencies.

## Usage

You can use Cobwebhook as part of a Plug pipeline as follows:

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

Takes a function that returns a list of valid secrets. On valid request, sets
`conn.body_params` and `conn.assigns.secret` and forwards request to the next
plug in the pipeline.

## For Contributers

This project only needs `elixir` in order to build. If you have the `nix`
package manager installed, you can run `nix-shell` to enter a shell with all
dependencies.

In order to build this project, run:

```
mix deps.get
mix
```

## About Serokell

Cobwebhook is maintained and funded with :heart: by [Serokell](https://serokell.io/). The names and logo for Serokell are trademark of Serokell OÜ.

We love open source software! See [our other projects](https://serokell.io/community?utm_source=github) or [hire us](https://serokell.io/hire-us?utm_source=github) to design, develop and grow your idea!
