# Docker Compose configuration for the installion of Tonic Textual

Note that installation requires access to the Tonic Textual docker container repository.  Reach out to support@tonic.ai to get your container repository login credentials.

# Setup
Rename the sample.env file to .env.  Inside the .env file you'll have to fill in the missing variables in order get Textual running.  The required values you must enter are

```
SOLAR_VERSION
ENVIRONMENT_NAME
SOLAR_DB_PASSWORD= #<FILL IN>
SOLAR_SECRET= #<FILL IN>
SOLAR_STATISTICS_SEED= #<FILL IN>
SOLAR_LICENSE= #<FILL IN>
```bash

Everything else is optional. Reach out to support@tonic.ai with any questions.

## Analytics

Release images do not include Amplitude credentials. To enable analytics, set
`AMPLITUDE_API_KEY` and `ANALYTIC_BACKEND_SALT` in `.env`.

Docker Compose passes these values to the `textual-api` and `textual-worker`
containers. They are intentionally not passed to ML, Roberta, ASR, log shipper,
database, or setup helper containers.
