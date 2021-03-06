---
layout: default
title: Security
nav_order: 5
has_children: true
has_toc: false
---

# Security

Open Distro for Elasticsearch includes the Security plugin for authentication and access control. This plugin provides features like:

- Node-to-node encryption
- Basic authentication
- Role-based access control
- Permission sets
- Index-, document-, and field-level security
- Audit logging of read and write operations
- Support for Active Directory, LDAP, Kerberos, and SAML
- Cross-cluster search
- Kibana multi-tenancy

The plugin includes demo certificates so that you can get up and running quickly, but you should [replace the demo certificates](../install/docker/#configure-elasticsearch) and [reconfigure `elasticsearch.yml`](tls-configuration) before using Open Distro for Elasticsearch in a production environment.

If you don't want to use the plugin, see [Disable security](disable).
