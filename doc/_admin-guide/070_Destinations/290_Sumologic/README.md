---
title: 'Sumo Logic destinations: sumologic-http() and
  sumologic-syslog()'
short_title: sumologic
id: adm-dest-sumologic
description: >-
    From version 3.27.1, the {{ site.product.short_name }}
    application can send log messages to Sumo Logic,
    a cloud-based log management and security analytics service, by
    using the sumologic-http() and sumologic-syslog() destinations.
---

## Prerequisites

Currently, using the sumologic-http() and sumologic-syslog()
destinations with {{ site.product.short_name }} has the following prerequisites:

- A Sumo Logic account.

    If you do not yet have a Sumo Logic account, visit the official
    Sumo Logic website, and click **Start free trial** to create an account.

    **NOTE:** A free trial version of the Sumo Logic account has limited
    functionalities and is only available for 90 days.
    {: .notice--info}

- A Cloud Syslog Source
    configured with your Sumo Logic account.

    For details, follow the configuration instructions under the
    Configure a Cloud Syslog Source section on the official Sumo Logic website.

    **NOTE:** Transport-level security (TLS) 1.2 over TCP is required.
    {: .notice--info}

- A Cloud Syslog Source Token (from the Cloud Syslog Source side).

- TLS set up on your Sumo Logic account.

    For detailed information about setting up TLS in your Sumo Logic
    account, see the description for setting up TLS on the Sumo Logic
    official website.

    **NOTE:** After you download the **DigiCert** certificate, make sure you follow the certificate setup steps under the syslog-ng
    section in Cloud Syslog Source chapter.
    {: .notice--info}

- Your Sumo Logic syslog client, configured to send data to the Sumo
    Logic cloud syslog service, by using {{ site.product.short_name }}.

    For detailed information, follow the instructions under the Send
    data to cloud syslog source with {{ site.product.short_name }} section on the official Sumo Logic website.

- A verified connection and client configuration with the Sumo Logic
    service.

    ![]({{ site.baseurl}}/assets/images/caution.png) **CAUTION:**
    To avoid potential data loss, One Identity strongly recommends that you verify your connection and client configuration with the Sumo Logic service before you start using the sumologic-http() or sumologic-syslog() destination
    with {{ site.product.short_name }} in a production environment.
    {: .notice--warning}

- (Optional) For using the sumologic-http() destination, you need a
    HTTP Hosted Collector configured in the Sumo Logic service.

    To configure a Hosted Collector, follow the configuration
    instructions under the Configure a Hosted Collector
    section on the official Sumo Logic website.

- (Optional) For using the sumologic-http() destination, you need the
    unique HTTP collector code you receive while configuring your Host
    Collector for HTTP requests.

## Limitations

Currently, using the sumologic-syslog() and sumologic-http()
destinations with {{ site.product.short_name }} has the following limitations:

- The minimum required version of {{ site.product.short_name }} is version 3.27.1.

- Message format must be in RFC-5424 compliant form. Messages over
    64KB in length are truncated.

    For more information about the message format limitations, see the
    Message format section on the official Sumo Logic website.

- 64 characters long Sumo Logic tokens must be passed in the message
    body.

    NOTE: Although RFC-5424 limits the structured data field
    (SD-ID) to 32 characters, Sumo Logic tokens are 64 characters long. If your
    logging client enforces the 32 characters length limit, you must
    pass the token in the message body.

## Declaration for the sumologic-http() destination

```config
destination d_sumo_http {
    sumologic-http(
    collector("ZaVnC4dhaV3_[...]UF2D8DRSnHiGKoq9Onvz-XT7RJG2FA6RuyE5z4A==")
    deployment("eu")
    tls(peer-verify(yes) ca-dir('/etc/syslog-ng/ca.d'))
    );
};
```

## Declaration for the sumologic-syslog() destination

```config
destination d_sumo_syslog {
    sumologic-syslog(
    token("rqf/bdxYVaBLFMoU39[...]CCC5jwETm@41123")
    deployment("eu")
    tls(peer-verify(yes) ca-dir('/etc/syslog-ng/ca.d'))
    );
};
```

## Using the sumologic() driver

To use the sumologic() driver, the scl.conf file must be included in
your {{ site.product.short_name }} configuration:

```config
@include "scl.conf"
```

**NOTE:** The sumologic() driver is actually a reusable configuration
snippet configured to send log messages using the network() and http()
destination by using a template. For details on using or writing such
configuration snippets, see Reusing configuration blocks.
You can find the source of the Sumo Logic configuration snippet on GitHub.
{: .notice--info}
