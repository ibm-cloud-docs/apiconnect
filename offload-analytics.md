---

copyright:
   years: 2024, 2026
lastupdated: "2026-07-02"

keywords: IBM Cloud, API Connect, V12 Reserved instance, analytics offload, Kafka, HTTP, offloading

subcollection: apiconnect

---

{{site.data.keyword.attribute-definition-list}}

# Offloading analytics data in {{site.data.keyword.apiconnect_short}} V12 Reserved
{: #offload-analytics}

Configure {{site.data.keyword.apiconnect_short}} V12 Reserved to offload analytics data to external systems so that you can view and manage the data using other analytics solutions.
{: shortdesc}

You can offload analytics data to a Kafka topic or to an HTTP endpoint. Both methods are configured from the **Settings** tile on the administration console Home page.

## Offloading analytics data to Kafka
{: #offload_kafka_v12ri-offload-analytics}

### Before you begin
{: #kafka_prereqs_v12ri-offload-analytics}

Before configuring Kafka offload, gather the following information about your Kafka instance:
- Topic name
- Kafka broker endpoints (at least one required)
- Credentials (username and password)

For more information about Kafka, see the [Apache Kafka documentation](https://kafka.apache.org/documentation/){: external}.

### Configuring Kafka offload
{: #kafka_config_v12ri-offload-analytics}

1. Log in to your V12 Reserved administration console.
2. On the Home page, click the **Settings** tile.
3. Click **Add destination**.
4. In the **Add offload destination** page, enter the following information:
   - **Name**: Enter a name for the offload destination.
   - **Offload Type**: Select **Kafka**.
   - **Topic**: Enter the Kafka topic name.
   - **Broker Endpoints**: Enter at least one broker endpoint URL for the Kafka instance.
   - **Choose a SASL mechanism**: Select the SASL mechanism that is configured in your Kafka account.
   - **Username and Password**: Enter the Kafka instance username and password.
   - **Assigned provider organizations**: Select the provider organizations whose data should be offloaded:
     - Select **Assign to all provider organizations** to offload data from all organizations.
     - Select **Select specific provider organizations** to choose specific organizations from the list.
   - **Fields to offload**: Choose which fields to include in the offloaded data:
     - Select **Offload all fields** to include all fields.
     - Select **Select specific fields to offload** to choose specific fields.

     **Note:** Your selection of fields applies to all existing offload destinations.

5. Click **Save** and wait 15–20 minutes for the offload to start.

   **Note:** After saving a new offload or editing an existing one, wait until the offload reaches **running** status before adding, editing, or deleting any offload. Refresh the settings page to view the latest status.

## Offloading analytics data to an HTTP endpoint
{: #offload_http_v12ri-offload-analytics}

### Before you begin
{: #http_prereqs_v12ri-offload-analytics}

Before configuring HTTP offload, gather the following information about your HTTP endpoint:
- HTTP endpoint URL
- Authentication credentials, depending on your authentication method:
    - **Client certificates**: `SSL_CERTIFICATE`, `SSL_CERTIFICATE_AUTHORITIES`, `SSL_KEY`
    - **Keystore/Truststore**: `SSL_KEYSTORE_PATH`, `SSL_TRUSTSTORE_PATH`
    - **Username/Password**: HTTP endpoint username and password

### Configuring HTTP endpoint offload
{: #http_config_v12ri-offload-analytics}

1. Log in to your V12 Reserved administration console.
2. On the Home page, click the **Settings** tile.
3. Click **Add destination**.
4. In the **Add offload destination** page, enter the following information:
   - **Name**: Enter a name for the offload destination.
   - **Offload Type**: Select **HTTP**.
   - **Authentication**: Select your authentication method and provide the required credentials:
     - **Client Certificates**: Upload the `SSL_CERTIFICATE`, `SSL_CERTIFICATE_AUTHORITIES`, and `SSL_KEY` files.
     - **Keystore/Truststore**: Upload the `SSL_KEYSTORE_PATH` and `SSL_TRUSTSTORE_PATH` files.
     - **Username/Password**: Enter the HTTP endpoint username and password.
   - **URL**: Enter your HTTP endpoint URL.
   - **Additional headers** (optional): Click **Add header** and enter header key-value pairs.
   - **Assigned provider organizations**: Select the provider organizations whose data should be offloaded.
   - **Fields to offload**: Choose which fields to include in the offloaded data.

5. Click **Save** and wait 15–20 minutes for the offload to start.
