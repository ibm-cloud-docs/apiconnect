---

copyright:
   years: 2024, 2026
lastupdated: "2026-06-30"

keywords: IBM Cloud, API Connect, V12 Reserved instance, gateways, DataPower, EEM, webMethods

subcollection: apiconnect

---

{{site.data.keyword.attribute-definition-list}}

# Managing gateways in {{site.data.keyword.apiconnect_short}} V12 Reserved
{: #v12rigateways}

{{site.data.keyword.apiconnect_short}} V12 Reserved supports multiple gateway types. The default IBM DataPower API Gateway is managed by IBM. You can deploy additional self-managed DataPower gateways and integrate with IBM Event Endpoint Management and webMethods API Gateway.
{: shortdesc}

## Default gateway
{: #default_gwy_v12ri-gateways}

{{site.data.keyword.apiconnect_short}} V12 Reserved deploys with the IBM DataPower API Gateway already configured. The gateway hosts published APIs, provides API endpoints for client applications, executes proxy invocations to back-end systems, and enforces API policies for client identification, security, and rate limiting. This default gateway is managed by IBM.

## Adding self-managed DataPower gateways
{: #self_mgd_gwy_v12ri-gateways}

You can deploy additional DataPower gateways for your V12 Reserved instance; for example, to distribute API endpoints for different purposes. Any gateways that you deploy are considered remote to the V12 Reserved deployment, and you are responsible for managing them.

To add a self-managed DataPower gateway:

1. Log in to your V12 Reserved administration console.
2. Click the **Download Gateway** tile on the Home page.
3. Select your environment and download the gateway package.
4. Install the gateway by following the instructions for your environment.
5. Generate certificates and configure the gateway, then register it with your V12 Reserved instance.

For detailed instructions, see [Adding self-managed gateways in V10 Reserved](https://www.ibm.com/docs/SSMNED_v10cloud/com.ibm.apic.ri_admin.doc/ri_gwy_intro.html){: external} (the gateway registration steps are the same for V12 Reserved).

### Generating certificates for a self-managed gateway
{: #gwy_certs_v12ri-gateways}

Before registering a gateway, generate the required certificates:

1. Generate certificates for the gateway using the instructions at [Generating certificates for a gateway](https://www.ibm.com/docs/SSMNED_v10cloud/com.ibm.apic.ri_admin.doc/ri_gwy_certs.html){: external}.
2. Set up authorizations for the certificates. For instructions, see [Setting up authorizations for certificates](https://www.ibm.com/docs/SSMNED_v10cloud/com.ibm.apic.ri_admin.doc/ri_gwy_certs_auth_svc.html){: external}.

### Generating an image pull secret (Kubernetes / OpenShift)
{: #pull_secret_v12ri-gateways}

To deploy a self-managed gateway on Kubernetes or OpenShift using the DataPower Operator, generate an image pull secret from the V12 Reserved administration console:

1. Log in to your V12 Reserved administration console.
2. On the Home page, click **Download Gateway**, or navigate to the gateway page.
3. Under **DataPower image registry credentials for Kubernetes/OCP pull secret**, click **Generate** (or **Regenerate** to replace existing credentials).
4. Apply the downloaded YAML secret in your Kubernetes or OpenShift cluster:
   ```bash
   kubectl apply -f <downloaded-secret-file>.yaml
   ```
   {: pre}

### Migrating certificates to Secrets Manager
{: #migrate_certs_v12ri-gateways}

If you need to migrate existing gateway certificates to IBM Secrets Manager, see [Migrating certificates to Secrets Manager](https://www.ibm.com/docs/SSMNED_v10cloud/com.ibm.apic.ri_admin.doc/ri_gwy_migrate_certs.html){: external}.

## Registering an Event Gateway Service (IBM Event Endpoint Management)
{: #eem_v12ri-gateways}

You can register an IBM Event Endpoint Management (EEM) instance as an Event Gateway Service in your V12 Reserved instance. This enables application developers to discover Kafka event endpoints and consume them through the event gateway.

### Before you begin
{: #eem_prereqs_v12ri-gateways}

Before registering the Event Gateway Service:
1. Download the Ingress CA certificate and retrieve the Platform API endpoint from the **Download Configuration** tab in the **Event Gateway** section on the IBM Cloud Manager home page.
2. Obtain TLS certificates for a TLS Client profile from your Event Endpoint Management instance. Locate the secret named `<event-manager-instance-name>-ibm-eem-manager` and copy the `ca.crt`, `tls.crt`, and `tls.key` values.
3. Configure Event Endpoint Management to trust {{site.data.keyword.apiconnect_short}} using the Ingress CA certificate.

### Registering the Event Gateway Service
{: #eem_register_v12ri-gateways}

1. Log in to your V12 Reserved administration console.
2. Set up a truststore with the CA certificates:
   - On the Home page, click the **TLS** tile.
   - In the **Truststores** section, click **Create**.
   - Enter a title and upload your `cluster-ca.pem` certificate.
   - Click **Save**.
3. Set up a keystore with the client key and certificates:
   - On the Home page, click the **TLS** tile.
   - In the **Keystores** section, click **Create**.
   - Enter a title, upload the client certificate (`manager-client.pem`) and client key (`manager-client-key.pem`).
   - Click **Save**.
4. Create a TLS Client profile using the truststore and keystore you created.
5. Navigate to the **Gateway** section and register the Event Gateway Service, specifying the EEM Manager endpoint and the TLS Client profile.

For complete instructions, see [Configure an Event Endpoint Management Manager as an Event Gateway Service](https://ibm.biz/eem-apic-config){: external}.

## Using webMethods API Gateway (on demand)
{: #wm_gateway_v12ri-gateways}

webMethods API Gateway is a secure, policy-driven runtime for managing and exposing APIs to external consumers. It enforces authentication, authorization, traffic management, and mediation policies, and provides a web-based administrative interface with built-in analytics.

webMethods API Gateway is available on demand. To enable it, contact IBM Support. Once enabled, it appears as an available gateway in your V12 Reserved administration console.

For usage and administration instructions, see the [webMethods API Gateway documentation](https://www.ibm.com/docs/en/api-connect/saas){: external}.
