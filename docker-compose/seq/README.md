### Seq Containerized Setup Guide

[Seq](https://docs.datalust.co/docs) is a real-time search and analysis server for structured application logs and traces. It features a well-designed user interface, a JSON event store, and a familiar query language, making it an efficient platform for detecting and diagnosing issues in complex applications and microservices.

### Prerequisites

- Ensure the Traefik container is running (in the same `Docker Network`) and is properly configured. You can find setup instructions in the [Traefik README]([https://github.com/amlucas0xff/boilerplates/docker-compose/traefik/README.md](https://github.com/amlucas0xff/boilerplates/docker-compose/traefik/README.md)).

> [!NOTE]
> Alternatively, you have the option to not use a reverse proxy. In this case, configure each service by adding the respective service ports and remove the Traefik label entries from the `compose.yaml` file.;

1. **Configuration**:
  - Rename the `.env.sample` file to `.env` and adjust the variables to suit your requirements.
  - Make sure to follow carefully the password instructions from the `.env` file.

2. **Deploy the Stack**:
  - Run the following command to deploy Seq
     
```shell
   docker compose up -d
```
  > Once deployed, Seq will be accessible according to the values defined in the `.env` file 

4. **Ingesting Events**:

   - To make use of Seq, you need to configure your applications to send events using one of the supported libraries:
     - Containers running other services can forward their logs to Seq using Docker's GELF (Graylog extended log format) log driver for easier log management.
     - For more information on supported libraries and ingestion methods, refer to the [Seq documentation](https://docs.datalust.co/docs).

  > [!NOTE]
  > **Alerting and Notifications**: Seq can send alerts and notifications based on the log data received, which can be configured to use various outputs like email, Slack, or other services.

### License
MIT License

