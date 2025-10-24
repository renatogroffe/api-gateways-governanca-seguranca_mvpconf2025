# api-gateways-governanca-seguranca_mvpconf2025
Conteúdos da apresentação "Governança e Segurança em APIs REST: tirando o melhor proveito de APIs Gateways!".

---

## Rate Limit por Subscription Key

Exemplo de uso da policy <rate-limit-by-key> (inbound):

```yaml
<policies>
    <inbound>
        <base />
        <rate-limit-by-key calls="5" renewal-period="15" counter-key="@(context.Subscription.Id)" />
    </inbound>
    <backend>
        <base />
    </backend>
    <outbound>
        <base />
    </outbound>
    <on-error>
        <base />
    </on-error>
</policies>
```

---

## Cache por Subscription Key

```yaml
<policies>
    <!-- Throttle, authorize, validate, cache, or transform the requests -->
    <inbound>
        <base />
        <cache-lookup vary-by-developer="false" vary-by-developer-groups="false" downstream-caching-type="none">
            <vary-by-header>Ocp-Apim-Subscription-Key</vary-by-header>
        </cache-lookup>
    </inbound>
    <!-- Control if and how the requests are forwarded to services  -->
    <backend>
        <base />
    </backend>
    <!-- Customize the responses -->
    <outbound>
        <base />
        <cache-store duration="10" cache-response="true" />
    </outbound>
    <!-- Handle exceptions and customize error responses  -->
    <on-error>
        <base />
    </on-error>
</policies>
```
---

Tokens JWT com Microsoft Entra ID

```yaml
    <inbound>
        <base />
        <validate-azure-ad-token tenant-id="id_tenant_microsofentraid">
            <client-application-ids>
                <application-id>id_appregistration</application-id>
            </client-application-ids>
        </validate-azure-ad-token>
    </inbound>
```
