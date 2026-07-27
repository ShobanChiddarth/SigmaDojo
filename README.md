# SigmaDojo - Sigma Rule Builder & Live Validation Engine for PWNDORA

**[Click Here for PROBLEM STATEMENT](./PROBLEM_STATEMENT.md)**

## Solution Overview

SigmaDojo is an interactive browser based hands-on learning platform that has 5 labs for teaching detection engineering. The labs present a problem statement and ask the uset to write a sigma rule to filter the logs and the platform can validate the rule, execute the challenge and calculate result.

Sigmadojo also has an optional playground where users can test a custom rule against a dataset picked by them. Additionally, there is another functionality to **transpile** a given valid sigma rule to **Splunk SPL** or **Sentinel KQL** that can be used in real systems.

The 5 labs/challenges are ready to be integrated with **PWNDORA** for teaching detection engineering to users.

## Architecture 

### Backend

The backend is written in FastAPI. It downloads the log datasets from the internet and saves them to a folder, and uses `sqlite` database to store and view the challenges metadata. It exposes the required endpoints defined in the problem statement.

**For more details and API docs of the backend, see:** [ShobanChiddarth/sigmadojo-backend](https://github.com/ShobanChiddarth/sigmadojo-backend)

### Database

Database requirements are very low as only a single table with static values are needed, and will never be updated after startup, so we went with `sqlite` for the database and the database file will be stored in the working directory from where the backend is being run. 

### Frontend

The frontend is written in Vite (React+Javascript). The container for the frontend loads an nginx.conf on runtime and can read environment variables passed down to it, which is how the backend URL is specified during startup.

**For more details of the frontend, see:** [ShobanChiddarth/sigmadojo-frontend](https://github.com/ShobanChiddarth/sigmadojo-frontend)

## Requirements

1. Docker
2. Docker Compose

## Steps to Run

1. Download this file: [docker-compose.yaml](./docker-compose.yaml)
2. `cd` into the repo where this file exists
3. Run the command `docker compose up -d`
4. Wait for a few minutes as the log datasets downloading takes a lot of time

## Verify

Visit [http://localhost:3000](http://localhost:3000) on your browser to view the app. Please note that it may not work immediately as the log datasets take a lot of time to download.

## References

1. [https://sigmahq.io/](https://sigmahq.io/)
2. [https://www.docker.com/](https://www.docker.com/)
3. [https://docs.docker.com/compose/](https://docs.docker.com/compose/)
