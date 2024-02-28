# cdpop

Pop open  cash drawer using http GET request

Use tornado to listen on configured port for http
or https requests to endpoints:

	GET /status	Return cash drawer status
	GET /open	Request cash drawer open

If authentication is configured, supply user and or auth
as query parameters, eg:

	GET /status?auth=Ricim8Knak

Requests to open drawer will return successfully (200) as
soon as possible, but will be processed in turn, once access
to the attached device is available. No feedback is provided for
an open request.

Requests for status will block until a valid status can be read
from the attached device. In the case of a hardware error,
status requests will return Internal Server Error (500).

## Usage

	$ cdpop [config.json]

## Requirements

   - python >= 3.9
   - tornado
   - posiflex-hidcd

## Configuration

Copy example config to a new file and edit as required.
Available configuration options:

  - port (int) TCP service port
  - cert (string) TLS certificate path (optional)
  - key (string) TLS private key path (optional)
  - auth (string) Authorisation key (optional)
  - user (string) Authorisation username (optional)
  - drawer (int) Cash drawer number (optional)
